[Back To Home](/)

# tk-clockins

> TK Clockins is still under development. Please keep an eye on our announcements channel for updates!

## Install

### 1. Dependencies

TK Spikes has 2 dependencies:

- QBCore
- tk-lib (Available from keymaster)

### 2. Starting resources

Ensure that `tk-lib` is in your resource folder. We reccommend putting all TK Studios resources in a folder called `[tk-studios]`.

Add `ensure [tk-studios]` to your server.cfg

Ensure the resource with `ensure tk-clockins`

### 3. Database Config

You will need to create a trigger in your database of choice. Ensure that your database name matches if you have chosen to change it. You will need to start the resource once to allow it to create the database to add the trigger to.

```sql
DELIMITER //

CREATE TRIGGER update_total_before_update
BEFORE UPDATE ON tk_clockins
FOR EACH ROW
BEGIN
    IF NEW.clockout IS NOT NULL THEN
        SET NEW.total = NEW.clockout - NEW.clockin;
    END IF;
END; //

DELIMITER ;
```

> If you encounter issues creating a trigger with sql, you can create it manually in phpMyAdmin using the reference below:

<div class="img-gallery">
    <img class="img-gallery-item" src="/assets/tk-clockins/trigger.png">
</div>

### 4. Reboot Resource

Ensure the resource with `ensure tk-clockins`

> You can get support with resources in the TK Studios Discord using the link in the top right!

## Config

### Database Table

> Database Table Name

```js
Config.DatabaseTable = "tk_clockins";
```

### Minimum Time

> Minimum time in ms for a clockin to count when being fetched using the built in exports.

```js
Config.MinimumTime = 30 * 1000; // Minimum time in order for a clock in to count. (IN MS)
```

### Jobs

> Array of jobs to record shifts for.

```js
Config.Jobs = ["police", "tow", "burgershot", "mechanic", "unemployed"];
```

## Server Exports

### isDepartmentClocked()

```js
/**
 * Checks if a department clockins are being recorded.
 *
 * @param {string} Department - The department to check.
 * @returns {boolean} - True if the department is clocked in, false otherwise.
 */
global.exports["tk-clockins"].isDepartmentClocked("police"); // true
```

### getPlayerHours()

```js
/**
 * Retrieves the total hours worked by a player for a specified number of days.
 *
 * @param {string} Identifier - The identifier of the player.
 * @param {number} [Days=7] - The number of days to fetch clockins for. Defaults to 7 if not provided.
 * @returns {Promise<Array<Object>>} - A promise that resolves to an array of objects containing job and totalTime.
 */
await global.exports["tk-clockins"].getPlayerHours("148764657107075072", 7);
```

### getPlayerClockins()

```js
/**
 * Retrieves player clock-ins based on the provided parameters.
 *
 * @param {string} Identifier - The identifier of the player.
 * @param {string} Job - The job for which clock-ins are retrieved.
 * @param {number} Days - The number of days to consider for clock-ins (default: 7).
 * @param {number} Limit - The maximum number of clock-ins to retrieve (default: 10).
 * @returns {Promise<Array<Object>>} An array of clock-in objects containing job, startTime, and totalTime.
 */
await global.exports["tk-clockins"].getPlayerClockins("148764657107075072", "police", 7, 20);
```

### getDepartmentClockinLeaderboard()

```js
/**
 * Retrieves the leaderboard for a specific job within a given time period.
 *
 * @param {string} Job - The job name.
 * @param {number} Days - The number of days to consider for the leaderboard. Defaults to 7 days if not provided.
 * @param {number} Limit - The maximum number of results to return. Defaults to 10 if not provided.
 * @returns {Promise<Array<Object>>} - The leaderboard data, containing the identifier, total time, and rank for each department.
 */
await global.exports["tk-clockins"].getDepartmentClockinLeaderboard("police", 7, 20);
```

### getGlobalClockinLeaderboard()

```js
/**
 * Fetches the leaderboard for the specified number of days.
 * If no number of days is provided, it fetches the leaderboard for the last 7 days.
 *
 * @param {number} Days - The number of days to fetch the leaderboard for.
 * @returns {Promise<Array<Object>>} - The leaderboard data, containing job and total time.
 */
await global.exports["tk-clockins"].getGlobalClockinLeaderboard(7);
```
