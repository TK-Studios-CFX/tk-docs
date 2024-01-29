[Back To Home](/)

# TK-Lib

TK-Lib is the core library for all TK Studios resources.

---

## Importing TK-Lib

**JS**

```js
const Lib = global.exports["tk-lib"].GetLib();
```

**LUA**

```lua
local Lib = exports["tk-lib"]:GetLib();
```

---

## Notifications

**JS**

```js
Lib.Functions.Notify(3, "success", "Test?", 3000); // Send an error notification to player 3 lasting for 3 seconds.
Lib.Functions.Notify(3, "error", "Do ya like jazz?", Lib.Time.Second * 5); // Send an error notification to player 3 lasting for 5 seconds.
```

**LUA**

```lua
Lib.Functions.Notify(3, 'success', 'Test?', 3000) -- Send an error notification to player 3 lasting for 3 seconds.
Lib.Functions.Notify(3, 'error', 'Do ya like jazz?', Lib.Time.Second * 5) -- Send an error notification to player 3 lasting for 5 seconds.
```

---

## Logger

**JS**

```js
const Logger = Lib.Functions.Logger("TK-Test", "Demo");

Logger.log("Hello World with TK-Lib");
Logger.warn("Warning with TK-Lib");
Logger.error("Error Message with TK-Lib");
Logger.success("Success Message with TK-Lib");
Logger.alert("Alert with TK-Lib");
Logger.debug("Debug Only Mode with TK-Lib");
Logger.trace("Stack Trace with TK-Lib");
```

**LUA**

```lua
local Logger = Lib.Functions.Logger("TK-Test", "Demo")

Logger.log("Hello World with TK-Lib")
Logger.warn("Warning with TK-Lib")
Logger.error("Error Message with TK-Lib")
Logger.success("Success Message with TK-Lib")
Logger.alert("Alert with TK-Lib")
Logger.debug("Debug Only Mode with TK-Lib")
Logger.trace("Stack Trace with TK-Lib")
```

---

## Items

**JS**

```js
let HasItem = Lib.Functions.HasItem(3, "weapon_combatpistol", 1); // Returns true if Server ID 3 has a combat pistol.

Lib.Functions.AddItem(3, "weapon_hatchet", 1); // Gives a hatchet to Server ID 3.
Lib.Functions.AddItem(3, "weapon_combatpistol", 1, 5, {}); // Gives 1 combat pistol to Server ID 3 in slot 5 with no metadata.

let ItemRemoved = Lib.Functions.RemoveItem(3, "weapon_hatchet", 1); // Removes 1 hatchet from Server ID 3.
```

**LUA**

```lua
local HasItem = Lib.Functions.HasItem(3, "weapon_combatpistol", 1) -- Returns true if Server ID 3 has a combat pistol.

Lib.Functions.AddItem(3, 'weapon_hatchet', 1) -- Gives a hatchet to Server ID 3.
Lib.Functions.AddItem(3, 'weapon_combatpistol', 1, 5, {}) -- Gives 1 combat pistol to Server ID 3 in slot 5 with no metadata.

local ItemRemoved = Lib.Functions.RemoveItem(3, 'weapon_hatchet', 1) -- Removes 1 hatchet from Server ID 3.
```

---

## Player List

**JS**

```js
let PlayersList = Lib.Functions.GetPlayersArray(); // [ 3, 14, 24 ] Array of Server IDs.
```

**LUA**

```lua
local PlayersList = Lib.Functions.GetPlayersArray() -- { 3, 14, 24 } Array of Server IDs.
```

---

## Routing Buckets

**JS**

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

---

## Player Identifiers

**JS**

```js
let DiscordID = Lib.Functions.GetPlayerIdentifier(3, "discord"); // Gets the discord identifier of Server ID 3.
```

**LUA**

```lua
local DiscordID = Lib.Functions.GetPlayerIdentifier(3, 'discord') -- Gets the discord identifier of Server ID 3.
```

---

## Time

**JS**

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

**LUA**

```lua
local Second = Lib.Time.Second -- 1 Second in MS
local Minute = Lib.Time.Minute -- 1 Minute in MS
local Hour = Lib.Time.Hour -- 1 Hour in MS
local Day = Lib.Time.Day -- 1 Day in MS
local Week = Lib.Time.Week -- 1 Week in MS
local Month = Lib.Time.Month -- 1 Month in MS
local Year = Lib.Time.Year -- 1 Year in MS

local CurrentEpoch = Lib.Time.GetEpoch() -- Current Epoch Time in MS
local FullReadableTime = Lib.Time.EpochToReadableDateString(CurrentEpoch) -- Readable Date String (Full)
local ShortReadableTime = Lib.Time.EpochToShortDateString(CurrentEpoch) -- DD/MM/YYYY Readable Date String (Short)
local ReadableDateTimeString = Lib.Time.EpochToReadableDateTimeString(CurrentEpoch) -- Full Date + Time

local ReadableTimeString = Lib.Time.MSToReadableTimeString(Hour * 3) -- 3h 0m 0s
```

---

## Maths

**JS**

```js
let DummyArray = [1, 2, 3];

Lib.Maths.AverageArray(DummyArray); // 2
Lib.Maths.MinArray(DummyArray); // 1
Lib.Maths.MaxArray(DummyArray); // 3

let Vec2 = Lib.Maths.Vector2(0, 0); // X, Y
let Vec4 = Lib.Maths.Vector3(4, 4, 4); // X, Y, Z
let Vec4 = Lib.Maths.Vector4(4, 4, 4, 270); // X, Y, Z, W

let Pos1 = Lib.Maths.Vector3(0, 0, 0); // X, Y, Z
let Pos2 = Lib.Maths.Vector3(4, 4, 4); // X, Y, Z

Lib.Maths.Distance2D(Pos1.x, Pos1.y, Pos2.x, Pos2.y); // Distance between 2 X,Y Coordinate Sets
Lib.Maths.DistanceVector2(Pos1, Pos2); // Distance between 2 vector2 coordinates.

Lib.Maths.Distance3D(Pos1.x, Pos1.y, Pos1.z, Pos2.x, Pos2.y, Pos2.z); // Distance between 2 X,Y,Z Coordinate Sets (X1, Y1, Z1, X2, Y2, Z2)
Lib.Maths.DistanceVector3(Pos1, Pos2); // Distance between 2 vector3 coordinates.
```

**LUA**

```lua
local DummyArray = { 1, 2, 3 }

Lib.Maths.AverageArray(DummyArray) -- 2
Lib.Maths.MinArray(DummyArray) -- 1
Lib.Maths.MaxArray(DummyArray) -- 3

local Pos1 = vector3(0, 0, 0)
local Pos2 = vector3(4, 4, 4)

-- It is faster to do calculations of distance between vectors with lua's natives so they have not been provided as examples as it is not encouraged.

Lib.Maths.Distance2D(Pos1.x, Pos1.y, Pos2.x, Pos2.y) -- Distance between 2 x, y Coordinate Sets

Lib.Maths.Distance3D(Pos1.x, Pos1.y, Pos1.z, Pos2.x, Pos2.y, Pos2.z) -- Distance between 2 x, y, z Coordinate Sets (X1, Y1, Z1, X2, Y2, Z2)
```

---

## Currency Formatting

Accepted Currencies are:

```md
USD, EUR, GBP, AUD, CAD, JPY, CHF, CNY, SEK, NZD, NOK, MXN, SGD, HKD, KRW, TRY, INR, RUB, BRL, ZAR, PLN
```

**JS**

```js
let Amount = 5000;
let Currency = "USD";
let FormattedCurrency = Lib.Maths.FormatAsCurrency(Amount, Currency); // $5,000.00
```

**LUA**

```lua
local Amount = 5000
local Currency = "USD"
local FormattedCurrency = Lib.Maths.FormatAsCurrency(Amount, Currency) -- $5,000.00
```

---

## Money

**JS**

```js
let source = 3;

let PlayerCash = Lib.Functions.GetMoney(3, "cash"); // Get players 'cash'
Lib.Functions.SetMoney(3, "cash", 100); // Set player's 'cash' to 100
Lib.Functions.AddMoney(3, "bank", 150); // Gives player $150 'bank' money
let Success = Lib.Functions.RemoveMoney(3, "bank", 150); // Removes $150 from player, returns false if player does not have enough money.
```

**LUA**

```lua
local source = 3

local PlayerCash = Lib.Functions.GetMoney(3, 'cash') -- Get players 'cash'
Lib.Functions.SetMoney(3, 'cash', 100) -- Set player's 'cash' to 100
Lib.Functions.AddMoney(3, 'bank', 150) -- Gives player $150 'bank' money
local Success = Lib.Functions.RemoveMoney(3, 'bank', 150) -- Removes $150 from player, returns false if player does not have enough money.
```

---

## Kicking Players

**JS**

```js
Lib.Functions.KickPlayer(3, "Attempted Abuse"); // Kick Server ID 3 for 'Attempted Abuse'
```

**LUA**

```lua
Lib.Functions.KickPlayer(3, 'Attempted Abuse') -- Kick Server ID 3 for 'Attempted Abuse'
```