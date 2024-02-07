[Back To Home](/)

# tk-lib

> TK-Lib is the core library for all TK Studios resources.

## Install

### 1. Dependencies

TK Weed has 2 dependencies:

- oxmysql (Comes with QBCore)
- QBCore

### 2. Inventory

Ensure `tk-lib/Server/Config/index.js` has the correct inventory configuration option set.

### 3. Starting resources

Ensure that `tk-lib` is in your resource folder. We reccommend putting all TK Studios resources in a folder called `[tk-studios]`.

Add `ensure [tk-studios]` to your server.cfg

Reboot your server

## Server Side Exports

> The following exports are for use in server side scripts. For client side exports please scroll down.

### Getting Started

#### Importing tk-lib

##### GetLib()

```js
const Lib = global.exports["tk-lib"].GetLib();
```

### Lib.DB

#### Run()

```js
/**
 * Executes a database query.
 *
 * @async
 * @param {string} Query - The SQL query to execute.
 * @param {Array} [Params] - The parameters to be used in the query.
 * @returns {Promise<Array>} - The result of the query.
 */
await Lib.DB.Run("DELETE FROM ? WHERE id = ?", ["db_name", 1]);
```

#### Get()

```js
/**
 * Executes a database query, returning 1 row or null.
 *
 * @async
 * @param {string} Query - The SQL query to execute.
 * @param {Array} [Params] - The parameters to be used in the query.
 * @returns {Promise<Object>} - The result of the query.
 */
await Lib.DB.Get("SELECT * FROM ? WHERE id = ?", ["db_name", 1]);
```

#### All()

```js
/**
 * Executes a database query, returning all matching rows.
 *
 * @async
 * @param {string} Query - The SQL query to execute.
 * @param {Array} [Params] - The parameters to be used in the query.
 * @returns {Promise<Array[Object]>} - The result of the query.
 */
await Lib.DB.All("SELECT * FROM ?", ["db_name"]);
```

### Lib.Functions

#### Logger

##### Logger()

```js
/**
 * Creates a new Logger instance.
 *
 * @param {string} resourceName - The name of the resource.
 * @param {string} fileName - The name of the file.
 */
const Logger = Lib.Functions.Logger(GetCurrentResourceName(), "Main");
```

##### Logger.log()

```js
Logger.log("Hello World with TK-Lib");
```

##### Logger.warn()

```js
Logger.warn("Hello World with TK-Lib");
```

##### Logger.error()

```js
Logger.error("Hello World with TK-Lib");
```

##### Logger.success()

```js
Logger.success("Hello World with TK-Lib");
```

##### Logger.alert()

```js
Logger.alert("Hello World with TK-Lib");
```

##### Logger.debug()

> Debug logs are only visible if `Config.Debug` is set to `true` in `tk-lib/server/config/index.js`

```js
Logger.debug("Hello World with TK-Lib");
```

##### Logger.trace()

> Trace logs trace the call stack showing where the log was triggered from.

```js
Logger.trace("Hello World with TK-Lib");
```

#### Timings

##### Wait()

```js
/**
 * Waits for the specified amount of time.
 *
 * @async
 * @param {number} ms - The number of milliseconds to wait.
 * @returns {Promise<boolean>} - A promise that resolves to true after the specified time has elapsed.
 */
await Lib.Functions.Wait(500); // Time in MS
```

#### Notifications

##### Notify()

```js
Lib.Functions.Notify(3, "success", "Test?", 3000); // Send an error notification to player 3 lasting for 3 seconds.
Lib.Functions.Notify(3, "error", "Do ya like jazz?", Lib.Time.Second * 5); // Send an error notification to player 3 lasting for 5 seconds.
```

#### Items

##### HasItem()

```js
let HasItem = Lib.Functions.HasItem(3, "weapon_combatpistol", 1); // Returns true if Server ID 3 has a combat pistol.
```

##### AddItem()

```js
Lib.Functions.AddItem(3, "weapon_hatchet", 1); // Gives a hatchet to Server ID 3.
Lib.Functions.AddItem(3, "weapon_combatpistol", 1, 5, {}); // Gives 1 combat pistol to Server ID 3 in slot 5 with no metadata.
```

##### RemoveItem()

```js
let ItemRemoved = Lib.Functions.RemoveItem(3, "weapon_hatchet", 1); // Removes 1 hatchet from Server ID 3.
```

#### Money

##### GetMoney()

```js
Lib.Functions.GetMoney(3, "cash");
```

##### SetMoney()

```js
Lib.Functions.SetMoney(3, "cash", 100); // Set player's 'cash' to 100
```

##### AddMoney()

```js
Lib.Functions.AddMoney(3, "bank", 150); // Gives player $150 'bank' money
```

##### RemoveMoney()

```js
let Success = Lib.Functions.RemoveMoney(3, "bank", 150); // Removes $150 from player, returns false if player does not have enough money.
```

#### Moderation

##### KickPlayer()

```js
Lib.Functions.KickPlayer(3, "Attempted Abuse"); // Kick Server ID 3 for 'Attempted Abuse'
```

#### Players

##### GetPlayersArray()

```js
let PlayersList = Lib.Functions.GetPlayersArray(); // [ 3, 14, 24 ] Array of Server IDs.
```

##### GetPlayerIdentifiers()

```js
/**
 * Retrieves the identifiers associated with a player.
 *
 * @param {string} src - The source of the player.
 * @returns {string[]} - An array of player identifiers.
 */
const Identifier = Lib.Functions.GetPlayerIdentifiers(3); // [ 'fivem:12345', 'discord:148764657107075072', ... ]
```

##### GetPlayerIdentifier()

```js
/**
 * Retrieves the player identifier based on the given source and identifier type.
 *
 * @param {string} src - The source of the player.
 * @param {string} identifier - The type of identifier to retrieve.
 * @returns {string|null} The player identifier, or null if not found.
 */
const Identifier = Lib.Functions.GetPlayerIdentifier(3, "discord"); // 'discord:148764657107075072'
```

##### GetStrippedPlayerIdentifier()

```js
/**
 * Retrieves the stripped player identifier based on the given identifier type.
 *
 * @param {string} src - The source of the player.
 * @param {string} identifier - The identifier type.
 * @returns {string|null} The stripped player identifier, or null if not found.
 */
const Identifier = Lib.Functions.GetStrippedPlayerIdentifier(3, "discord"); // '148764657107075072'
```

### Lib.Buckets

```js
// Players
let src = 3;
let BucketID = Lib.Buckets.CreateRoutingBucket(false, "strict"); // Creates a new routing bucket with AI Population disabled & entity lockdown mode as strict. Options are ['strict', 'relaxed', 'inactive']
let { ID, PopulationEnabled, EntityLockdownMode } = Lib.Buckets.GetRoutingBucket(BucketID); // Fetch bucket object.

Lib.Buckets.SetPlayerBucket(src, BucketID);
Lib.Buckets.ClearPlayerRoutingBucket(src); // Return player to default routing bucket.

// Entities
let vehicle = 14281;
Lib.Buckets.SetEntityBucket(vehicle, BucketID);
```

### Lib.Time

```js
const Second = Lib.Time.Second; // 1 Second in MS
const Minute = Lib.Time.Minute; // 1 Minute in MS
const Hour = Lib.Time.Hour; // 1 Hour in MS
const Day = Lib.Time.Day; // 1 Day in MS
const Week = Lib.Time.Week; // 1 Week in MS
const Month = Lib.Time.Month; // 1 Month in MS
const Year = Lib.Time.Year; // 1 Year in MS

const CurrentEpoch = Lib.Time.GetEpoch(); // Current Epoch Time in MS
const FullReadableTime = Lib.Time.EpochToReadableDateString(CurrentEpoch); // Readable Date String (Full)
const ShortReadableTime = Lib.Time.EpochToShortDateString(CurrentEpoch); // DD/MM/YYYY Readable Date String (Short)
const ReadableDateTimeString = Lib.Time.EpochToReadableDateTimeString(CurrentEpoch); // Full Date + Time

const ReadableTimeString = Lib.Time.MSToReadableTimeString(Hour * 3); // 3h 0m 0s
```

### Lib.Maths

#### Arrays

##### AverageArray()

```js
Lib.Maths.AverageArray([1, 2, 3]); // 2
```

##### MinArray()

```js
Lib.Maths.MinArray([1, 2, 3]); // 1
```

##### MaxArray()

```js
Lib.Maths.MaxArray([1, 2, 3]); // 3
```

#### Vectors

##### Vector2()

```js
let Vec2 = Lib.Maths.Vector2(0, 0); // X, Y
```

##### Vector3()

```js
let Vec4 = Lib.Maths.Vector3(4, 4, 4); // X, Y, Z
```

##### Vector4()

```js
let Vec4 = Lib.Maths.Vector4(4, 4, 4, 270); // X, Y, Z, W
```

#### Distance

##### Distance2D()

```js
let Pos1 = Lib.Maths.Vector2(0, 0); // X, Y
let Pos2 = Lib.Maths.Vector2(4, 4); // X, Y

Lib.Maths.Distance2D(Pos1.x, Pos1.y, Pos2.x, Pos2.y); // Distance between 2 X,Y Coordinate Sets
```

##### DistanceVector2()

```js
let Pos1 = Lib.Maths.Vector2(0, 0); // X, Y
let Pos2 = Lib.Maths.Vector2(4, 4); // X, Y

Lib.Maths.DistanceVector2(Pos1, Pos2); // Distance between 2 vector2 coordinates.
```

##### Distance3D()

```js
let Pos1 = Lib.Maths.Vector3(0, 0, 0); // X, Y, Z
let Pos2 = Lib.Maths.Vector3(4, 4, 4); // X, Y, Z

Lib.Maths.Distance3D(Pos1.x, Pos1.y, Pos1.z, Pos2.x, Pos2.y, Pos2.z); // Distance between 2 X,Y,Z Coordinate Sets (X1, Y1, Z1, X2, Y2, Z2)
```

##### DistanceVector3()

```js
let Pos1 = Lib.Maths.Vector3(0, 0, 0); // X, Y, Z
let Pos2 = Lib.Maths.Vector3(4, 4, 4); // X, Y, Z

Lib.Maths.DistanceVector3(Pos1, Pos2); // Distance between 2 vector3 coordinates.
```

#### Currency

##### FormatAsCurrency()

> Accepted Currencies are:
> USD, EUR, GBP, AUD, CAD, JPY, CHF, CNY, SEK, NZD, NOK, MXN, SGD, HKD, KRW, TRY, INR, RUB, BRL, ZAR, PLN

```js
Lib.Maths.FormatAsCurrency(5000, "USD"); // $5,000.00
```

## Client Side Exports

> The following exports are for use in client side scripts. For server side exports please scroll up.

### Getting Started

#### Importing tk-lib

##### GetLib()

```js
const Lib = global.exports["tk-lib"].GetLib();
```

### Lib.Functions

#### Object Placer

```js
let Coords = await Lib.Functions.ObjectPlacementUI("object_name"); // Returns false if invalid coords or cancelled.
```

#### Logger

##### Logger()

```js
/**
 * Creates a new Logger instance.
 *
 * @param {string} resourceName - The name of the resource.
 * @param {string} fileName - The name of the file.
 */
const Logger = Lib.Functions.Logger(GetCurrentResourceName(), "Main");
```

##### Logger.log()

```js
Logger.log("Hello World with TK-Lib");
```

##### Logger.warn()

```js
Logger.warn("Hello World with TK-Lib");
```

##### Logger.error()

```js
Logger.error("Hello World with TK-Lib");
```

##### Logger.success()

```js
Logger.success("Hello World with TK-Lib");
```

##### Logger.alert()

```js
Logger.alert("Hello World with TK-Lib");
```

##### Logger.debug()

> Debug logs are only visible if `Config.Debug` is set to `true` in `tk-lib/server/config/index.js`

```js
Logger.debug("Hello World with TK-Lib");
```

#### Timings

##### Wait()

```js
/**
 * Waits for the specified amount of time.
 *
 * @async
 * @param {number} ms - The number of milliseconds to wait.
 * @returns {Promise<boolean>} - A promise that resolves to true after the specified time has elapsed.
 */
await Lib.Functions.Wait(500); // Time in MS
```
