[Back To Home](/)

# tk-lib

> TK-Lib is the core library for all TK Studios resources.

## Getting Started

### Importing tk-lib

#### GetLib()

```js
const Lib = global.exports["tk-lib"].GetLib();
```

## Lib.Functions

### Logger

#### Logger()

```js
/**
 * Creates a new Logger instance.
 *
 * @param {string} resourceName - The name of the resource.
 * @param {string} fileName - The name of the file.
 */
const Logger = Lib.Functions.Logger(GetCurrentResourceName(), "Main");
```

#### Logger.log()

```js
Logger.log("Hello World with TK-Lib");
```

#### Logger.warn()

```js
Logger.warn("Hello World with TK-Lib");
```

#### Logger.error()

```js
Logger.error("Hello World with TK-Lib");
```

#### Logger.success()

```js
Logger.success("Hello World with TK-Lib");
```

#### Logger.alert()

```js
Logger.alert("Hello World with TK-Lib");
```

#### Logger.debug()

> Debug logs are only visible if `Config.Debug` is set to `true` in `tk-lib`

```js
Logger.debug("Hello World with TK-Lib");
```

#### Logger.trace()

> Trace logs trace the call stack showing where the log was triggered from.

```js
Logger.trace("Hello World with TK-Lib");
```

### Notifications

#### Notify()

```js
Lib.Functions.Notify(3, "success", "Test?", 3000); // Send an error notification to player 3 lasting for 3 seconds.
Lib.Functions.Notify(3, "error", "Do ya like jazz?", Lib.Time.Second * 5); // Send an error notification to player 3 lasting for 5 seconds.
```

### Items

#### HasItem()

```js
let HasItem = Lib.Functions.HasItem(3, "weapon_combatpistol", 1); // Returns true if Server ID 3 has a combat pistol.
```

#### AddItem()

```js
Lib.Functions.AddItem(3, "weapon_hatchet", 1); // Gives a hatchet to Server ID 3.
Lib.Functions.AddItem(3, "weapon_combatpistol", 1, 5, {}); // Gives 1 combat pistol to Server ID 3 in slot 5 with no metadata.
```

#### RemoveItem()

```js
let ItemRemoved = Lib.Functions.RemoveItem(3, "weapon_hatchet", 1); // Removes 1 hatchet from Server ID 3.
```

### Money

#### GetMoney()

```js
Lib.Functions.GetMoney(3, "cash");
```

#### SetMoney()

```js
Lib.Functions.SetMoney(3, "cash", 100); // Set player's 'cash' to 100
```

#### AddMoney()

```js
Lib.Functions.AddMoney(3, "bank", 150); // Gives player $150 'bank' money
```

#### RemoveMoney()

```js
let Success = Lib.Functions.RemoveMoney(3, "bank", 150); // Removes $150 from player, returns false if player does not have enough money.
```

### Moderation

#### KickPlayer()

```js
Lib.Functions.KickPlayer(3, "Attempted Abuse"); // Kick Server ID 3 for 'Attempted Abuse'
```

### Players

#### GetPlayersArray()

```js
let PlayersList = Lib.Functions.GetPlayersArray(); // [ 3, 14, 24 ] Array of Server IDs.
```

#### GetPlayerIdentifier()

```js
let DiscordID = Lib.Functions.GetPlayerIdentifier(3, "discord"); // Gets the discord identifier of Server ID 3.
```

## Lib.Buckets

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

## Lib.Time

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

## Lib.Maths

### Arrays

#### AverageArray()

```js
Lib.Maths.AverageArray([1, 2, 3]); // 2
```

#### MinArray()

```js
Lib.Maths.MinArray([1, 2, 3]); // 1
```

#### MaxArray()

```js
Lib.Maths.MaxArray([1, 2, 3]); // 3
```

### Vectors

#### Vector2()

```js
let Vec2 = Lib.Maths.Vector2(0, 0); // X, Y
```

#### Vector3()

```js
let Vec4 = Lib.Maths.Vector3(4, 4, 4); // X, Y, Z
```

#### Vector4()

```js
let Vec4 = Lib.Maths.Vector4(4, 4, 4, 270); // X, Y, Z, W
```

### Distance

#### Distance2D()

```js
let Pos1 = Lib.Maths.Vector2(0, 0); // X, Y
let Pos2 = Lib.Maths.Vector2(4, 4); // X, Y

Lib.Maths.Distance2D(Pos1.x, Pos1.y, Pos2.x, Pos2.y); // Distance between 2 X,Y Coordinate Sets
```

#### DistanceVector2()

```js
let Pos1 = Lib.Maths.Vector2(0, 0); // X, Y
let Pos2 = Lib.Maths.Vector2(4, 4); // X, Y

Lib.Maths.DistanceVector2(Pos1, Pos2); // Distance between 2 vector2 coordinates.
```

#### Distance3D()

```js
let Pos1 = Lib.Maths.Vector3(0, 0, 0); // X, Y, Z
let Pos2 = Lib.Maths.Vector3(4, 4, 4); // X, Y, Z

Lib.Maths.Distance3D(Pos1.x, Pos1.y, Pos1.z, Pos2.x, Pos2.y, Pos2.z); // Distance between 2 X,Y,Z Coordinate Sets (X1, Y1, Z1, X2, Y2, Z2)
```

#### DistanceVector3()

```js
let Pos1 = Lib.Maths.Vector3(0, 0, 0); // X, Y, Z
let Pos2 = Lib.Maths.Vector3(4, 4, 4); // X, Y, Z

Lib.Maths.DistanceVector3(Pos1, Pos2); // Distance between 2 vector3 coordinates.
```

### Currency

#### FormatAsCurrency()

> Accepted Currencies are:
> USD, EUR, GBP, AUD, CAD, JPY, CHF, CNY, SEK, NZD, NOK, MXN, SGD, HKD, KRW, TRY, INR, RUB, BRL, ZAR, PLN

```js
Lib.Maths.FormatAsCurrency(5000, "USD"); // $5,000.00
```
