[Back To Home](/)

# TK Weed

<img class="img-center" src="./assets/tk-weed/banner.PNG">

<div class="img-gallery">
	<img class="img-gallery-item" src="./assets/tk-weed/1.PNG">
	<img class="img-gallery-item" src="./assets/tk-weed/2.PNG">
	<img class="img-gallery-item" src="./assets/tk-weed/3.PNG">
	<img class="img-gallery-item" src="./assets/tk-weed/4.PNG">
	<img class="img-gallery-item" src="./assets/tk-weed/5.PNG">
	<img class="img-gallery-item" src="./assets/tk-weed/6.PNG">
	<img class="img-gallery-item" src="./assets/tk-weed/7.PNG">
	<img class="img-gallery-item" src="./assets/tk-weed/8.PNG">
	<img class="img-gallery-item" src="./assets/tk-weed/9.PNG">
	<img class="img-gallery-item" src="./assets/tk-weed/10.PNG">
</div>

> TK Weed is a highly configurable weed farming, extraction and cooking resource with multiple growth stages, custom props and support for infinite custom strains of weed.

> You can enable debugging for TK Studios resources by enabling the `Config.Debug` option in `tk-lib`.

## Install

### 1. Dependencies

TK Weed has 4 dependencies:

- oxmysql (Comes with QBCore)
- QBCore
- tk-lib (Available from keymaster)
- n3-props (Available from keymaster)

### 2. Inventory

Copy the config from `tk-weed/install/items/items.md` to `QBCore/Shared/items.lua`

Copy the images from `tk-weed/install/images` to your inventory resource.

Ensure `tk-lib/Server/Config/index.js` has the correct inventory configuration option set.

### 3. Starting resources

Ensure that `tk-lib` & `n3-props` are in your resource folder. We reccommend putting all TK Studios resources in a folder called `[tk-studios]`.

Add `ensure [tk-studios]` to your server.cfg

Reboot your server

## Config

### Database Config

> These config options are used to set the database names for each table. It is extremely unlikely that you will ever need to touch these. Edit at your own risk!

```js
Config.DB_Planters = "tk_weed_planters";
Config.DB_Tables = "tk_weed_tables";
Config.DB_Kitchens = "tk_weed_kitchens";
```

### Scope Interval

> This value lets you set the update interval for scope in milliseconds, We reccommend having this between 5000-15000 to ensure a seamless experience for players.

```js
Config.UpdateScopeInterval = 5000;
```

### Language

> Config.Lang has all messages used throughout the resource. This allows you to customise messages or translate the resource into difference languages.

```js
Config.Lang = {};
```

### Soil

```js
// Soil
Config.Soil = {}; // Do Not Touch
Config.Soil.Name = "Weed Soil"; // The name of "Soil" when reffered to in notifications etc.
Config.Soil.Enabled = true; // Is soil required for planters to grow weed?
Config.Soil.Item = "weed_soil"; // Item name for soil, you can change this to your own item or use ours!
Config.Soil.Uses = 5; // The amount of uses each "soil" item has.
Config.Soil.Duration = 5000; // Time in MS to refill soil
Config.Soil.AnimDict = "amb@world_human_gardener_plant@female@base"; // Animation dictionary for refilling soil
Config.Soil.Anim = "base_female"; // Animation name for refilling soil
```

### Fertilizer

```js
// Fertilizer
Config.Fertilizer = {}; // Do Not Touch
Config.Fertilizer.Name = "Weed Fertilizer"; // The name of "Fertilizer" when reffered to in notifications etc.
Config.Fertilizer.Enabled = true; // Can fertilizer be used to speed up weed planter growth rate.
Config.Fertilizer.Item = "weed_fertilizer"; // Item name for fertilizer, you can change this to your own item or use ours!
Config.Fertilizer.Rate = 0.8; // The rate of growth multiplier when fertilizer is in use.
Config.Fertilizer.Uses = 3; // The uses per fertilizer item
Config.Fertilizer.Duration = 5000; // Time in MS to refill fertilizer
Config.Fertilizer.AnimDict = "amb@world_human_gardener_plant@female@base"; // Animation dictionary for refilling fertilizer
Config.Fertilizer.Anim = "base_female"; // Animation name for refilling fertilizer
```

### Shears

```js
// Shears
Config.Shears = {}; // Do Not Touch
Config.Shears.Name = "Weed Shears"; // The name of "Weed Shears" when reffered to in notifications etc.
Config.Shears.Item = "weed_shears"; // Item name for weed shears, you can change this to your own item or use ours!
Config.Shears.Duration = 8000; // Time in MS to harvest weed buds.
Config.Shears.AnimDict = "anim@amb@business@weed@weed_inspecting_lo_med_hi@"; // Animation dictionary for harvesting weed buds.
Config.Shears.Anim = "weed_crouch_checkingleaves_idle_01_inspector"; // Animation name for harvesting weed buds.
```

### Storage Jars

```js
// Storage Jars
Config.Jars = {}; // Do Not Touch
Config.Jars.Name = "Empty Weed Jar"; // The name of "Empty Weed Jar" when reffered to in notifications etc.
Config.Jars.Item = "weed_jar"; // Item name for an empty jar, you can change this to your own item or use ours!
Config.Jars.ExtractBudCount = 10; // Buds needed to extract weed oil
Config.Jars.BudCount = 100; // Buds needed to make weed jar
Config.Jars.Open = {}; // Do Not Touch
Config.Jars.Open.Duration = 5000; // Duration for opening a weed jar full of buds
Config.Jars.Open.AnimDict = "mp_arresting"; // Anim Dict for opening a jar
Config.Jars.Open.Anim = "a_uncuff"; // Anim for opening a jar
Config.Jars.Pack = {}; // Do Not Touch
Config.Jars.Pack.Duration = 8000; // Duration for packing a weed jar with buds
Config.Jars.Pack.AnimDict = "mp_arresting"; // Anim Dict for packing a weed jar with buds
Config.Jars.Pack.Anim = "a_uncuff"; // Anim for packing a weed jar with buds
Config.Jars.Extract = {}; // Do Not Touch
Config.Jars.Extract.Duration = 20000; // Duration for extracting weed oil into a jar
Config.Jars.Extract.AnimDict = "mp_arresting"; // Anim Dict for extracting weed oil into a jar
Config.Jars.Extract.Anim = "a_uncuff"; // Anim for extracting weed oil into a jar
```

### Edibles

```js
Config.Edibles = {}; // Do Not Touch
Config.Edibles.Brownies = {}; // Do Not Touch
Config.Edibles.Brownies.Type = "Brownies"; // Do Not Touch
Config.Edibles.Brownies.Item = "weed_brownie_mix"; // Item for brownie mix
Config.Edibles.Brownies.Duration = 20000; // Duration to make a set of brownies
Config.Edibles.Brownies.RequiredJars = 1; // Required jars of weed oil to make a batch of brownies
Config.Edibles.Brownies.RequiredMixes = 1; // Required brownie mixes to make a batch of brownies
Config.Edibles.Brownies.ItemsGiven = 5; // Brownies given per batch made
Config.Edibles.Brownies.AnimDict = "anim@amb@business@weed@weed_inspecting_lo_med_hi@"; // Anim Dict for making brownies
Config.Edibles.Brownies.Anim = "weed_crouch_checkingleaves_idle_01_inspector"; // Anim for making brownies
Config.Edibles.Gummies = {}; // Do Not Touch
Config.Edibles.Gummies.Type = "Gummies"; // Do Not Touch
Config.Edibles.Gummies.Item = "weed_gummy_mix"; // Item for gummy mix
Config.Edibles.Gummies.Duration = 30000; // Duration to make a set of gummies
Config.Edibles.Gummies.RequiredJars = 1; // Required jars of weed oil to make a batch of gummies
Config.Edibles.Gummies.RequiredMixes = 1; // Required gummy mixes to make a batch of gummies
Config.Edibles.Gummies.ItemsGiven = 5; // Gummies given per batch made
Config.Edibles.Gummies.AnimDict = "anim@amb@business@weed@weed_inspecting_lo_med_hi@"; // Anim Dict for making gummies
Config.Edibles.Gummies.Anim = "weed_crouch_checkingleaves_idle_01_inspector"; // Anim Dict for making gummies
```

### Planter Animations

```js
// Global Planter Config
Config.Planter = {}; // Do Not Touch
Config.Planter.Place = {}; // Do Not Touch
Config.Planter.Place.Duration = 5000; // Duration to place a weed planter
Config.Planter.Place.AnimDict = "amb@world_human_gardener_plant@female@base"; // Anim Dict for placing a weed planter
Config.Planter.Place.Anim = "base_female"; // Anim for placing a weed planter
Config.Planter.Pickup = {}; // Do Not Touch
Config.Planter.Pickup.Duration = 5000; // Duration for picking up a weed planter
Config.Planter.Pickup.AnimDict = "amb@world_human_gardener_plant@female@base"; // Anim Dict for picking up a weed planter
Config.Planter.Pickup.Anim = "base_female"; // Anim for picking up a weed planter
```

### Weed Planters

> Permanent weed planters can only be placed and removed with commands. This allows you to set up public weed farms around your server to help new players get started.

```js
// Weed Planters Config - Tiers are Permenant, Basic, Enhanced and Advanced.
Config.Planters = {}; // Do Not Touch

Config.Planters.Basic = {}; // Do Not Touch
Config.Planters.Basic.Name = "Basic Weed Planter"; // Name of the weed planter
Config.Planters.Basic.Item = "weed_planter_basic"; // Item for the weed planter
Config.Planters.Basic.Rate = 1000 * 60 * 15; // 15 Minutes Per Tier
Config.Planters.Basic.RGB = [38, 255, 49]; // R, G, B values out of 255.
```

### Weed Tables

> Permanent weed tables can only be placed and removed with commands. This allows you to set up public weed farms around your server to help new players get started.

```js
Config.Tables = {}; // Do Not Change

Config.Tables.Basic = {}; // Do Not Change
Config.Tables.Basic.Item = "weed_table_basic";
Config.Tables.Basic.Name = "Basic Weed Table";
Config.Tables.Basic.RGB = [38, 255, 49];
Config.Tables.Basic.Use = {}; // Do Not Change
Config.Tables.Basic.Use.Duration = 5000; // Time it takes to process a batch of weed in MS
Config.Tables.Basic.Use.MaxConcurrentProcesses = 2;
Config.Tables.Basic.Use.RequiredBuds = 3;
Config.Tables.Basic.Use.OutputBaggys = 1;
Config.Tables.Basic.Use.AnimDict = "mini@repair"; // Animation Dictionary for processing a batch of weed
Config.Tables.Basic.Use.Anim = "fixing_a_ped"; // Animation for processing a batch of weed
Config.Tables.Basic.Place = {}; // Do Not Change
Config.Tables.Basic.Place.Duration = 5000;
Config.Tables.Basic.Place.AnimDict = "mini@repair"; // Animation Dictionary for placing a weed table
Config.Tables.Basic.Place.Anim = "fixing_a_ped"; // Animation for placing a basic weed table
Config.Tables.Basic.Pickup = {}; // Do Not Change
Config.Tables.Basic.Pickup.Duration = 5000;
Config.Tables.Basic.Pickup.AnimDict = "mini@repair"; // Animation Dictionary for picking up a weed table
Config.Tables.Basic.Pickup.Anim = "fixing_a_ped"; // Animation for picking up a basic weed table
```

### Kitchens

> Permanent weed kitchens can only be placed and removed with commands. This allows you to set up public weed farms around your server to help new players get started.

```js
Config.Kitchens = {}; // Do Not Change

Config.Kitchens.Basic = {}; // Do Not Change
Config.Kitchens.Basic.Item = "weed_kitchen_basic"; // Item name for basic weed kitchen
Config.Kitchens.Basic.Name = "Basic Weed Kitchen"; // Name for notifications and progress bars
Config.Kitchens.Basic.RGB = [38, 255, 49]; // R, G, B values out of 255
Config.Kitchens.Basic.Use = {}; // Do Not Change
Config.Kitchens.Basic.Use.Duration = 5000; // Time it takes to process a batch of weed in MS
Config.Kitchens.Basic.Use.MaxConcurrentProcesses = 2; // Maximum batches to bake simultaneously
Config.Kitchens.Basic.Use.RequiredBuds = 10; // Required buds to extract weed oil
Config.Kitchens.Basic.Use.OutputOil = 1; // Output oil after extraction process
Config.Kitchens.Basic.Use.AnimDict = "mini@repair"; //"Animation Dictionary for processing a batch of weed
Config.Kitchens.Basic.Use.Anim = "fixing_a_ped"; //"Animation for processing a batch of weed
Config.Kitchens.Basic.Place = {}; // Do Not Change
Config.Kitchens.Basic.Place.Duration = 5000; // Duration for placing a weed kitchen
Config.Kitchens.Basic.Place.AnimDict = "mini@repair"; //"Animation Dictionary for placing a weed table
Config.Kitchens.Basic.Place.Anim = "fixing_a_ped"; //"Animation for placing a basic weed table
Config.Kitchens.Basic.Pickup = {}; // Do Not Change
Config.Kitchens.Basic.Pickup.Duration = 5000; // Duration for picking up a weed kitchen
Config.Kitchens.Basic.Pickup.AnimDict = "mini@repair"; //"Animation Dictionary for picking up a weed table
Config.Kitchens.Basic.Pickup.Anim = "fixing_a_ped"; //"Animation for picking up a basic weed table
```

### Planting

```js
Config.Planting = {}; // Do Not Change
Config.Planting.Duration = 8000; // Time in MS to plant weed seed.
Config.Planting.AnimDict = "amb@world_human_gardener_plant@female@base"; // Anim Dict for planting a seed
Config.Planting.Anim = "base_female"; // Anim for planting a seed
```

### Rolling Joints

```js
Config.Joints = {}; // Do Not Change
Config.Joints.Duration = 5000; // Duration for rolling a joint
Config.Joints.RequiredBaggies = 1; // Required baggies to roll a joint
Config.Joints.AnimDict = "mp_arresting"; // Anim Dict for rolling a joint
Config.Joints.Anim = "a_uncuff"; // Anim for rolling a joint
```

### Rolling Blunts

```js
Config.Blunts = {}; // Do Not Change
Config.Blunts.Duration = 5000; // Duration for rolling a blunt
Config.Blunts.RequiredBaggies = 3; // Required baggies for rolling a blunt
Config.Blunts.AnimDict = "mp_arresting"; // Anim Dict for rolling a blunt
Config.Blunts.Anim = "a_uncuff"; // Anim for rolling a blunt
```

### Emptying Pots

```js
Config.EmptyPot = {}; // Do Not Change
Config.EmptyPot.Duration = 2500; // Duration for emptying weed planters
Config.EmptyPot.AnimDict = "amb@world_human_gardener_plant@female@base"; // Anim Dict for emptying weed planters
Config.EmptyPot.Anim = "base_female"; // Anim for emptying weed planters
```

### Weed Strains

> TK Weed supports infinite strains of weed. We provide 6 default strains preconfigured for ease of use.

```js
Config.Strains = [];

Config.Strains.push({
	name: "Amnesia", // Name of the strain
	item: "weed_amnesia", // Item for weed baggy
	bud: "weed_amnesia_bud", // Item for weed bud
	seed: "weed_amnesia_seed", // Item for weed seed
	joint: "weed_amnesia_joint", // Item for joint
	blunt: "weed_amnesia_blunt", // Item for blunt
	jar: "weed_amnesia_jar", // Item for jar of bud
	oil: "weed_amnesia_oil", // Item for jar of extracted oil
	brownie: "weed_amnesia_brownie", // Item for brownie edible
	gummy: "weed_amnesia_gummy", // Item for gummy edible
	hash: "weed_amnesia_hash", // Item for hash

	Effects: {
		HealthBoost: [10, 20], // Joint vs Blunt values for health boost
		HealthNegate: [0, 0], // Joint vs Blunt values for health removal
		ArmorBoost: [10, 20], // Joint vs Blunt values for armor boost
		ArmorNegate: [0, 0], // Joint vs Blunt values for armor removal
		SpeedBoost: [10, 20], // Joint vs Blunt values for speed boost
		ScreenShake: [5, 7], // Joint vs Blunt values for screen shake
		Timecycle: ["spectator5", 1.1, 1.3], // Time Cycle Modifier (Screen Effect Layer 1) for Joints vs Blunts
		Timecycle2: ["", 10, 20], // Time Cycle 2 Modifier (Screen Effect Layer 2) for Joints vs Blunts
		PostFX: ["", ""], // Post FX to run for Joints vs Blunts
		BloodOverlay: [false, true], // Should blood overlay be enabled for Joints vs Blunts
		Drunk: [true, true], // Should drunk walk be enabled for Joints vs Blunts
	},

	Harvest: {
		Buds: [1, 7], // [MinimumHarvest, MaximumHarvest] for buds per planter harvest.
		Seeds: [0, 3], // [MinimumHarvest, MaximumHarvest] for seeds per planter harvest.
	},
});
```

### Admin Commands

> You can configure the commands for admins to add or remove weed planters here

```js
Config.Commands = {};

// Clear any active weed effects from yourself.
Config.Commands.ClearWeedEffects = {}; // Do Not Touch
Config.Commands.ClearWeedEffects.Command = "ClearWeedEffects"; // Command Name
Config.Commands.ClearWeedEffects.Ace = "qbdev"; // Permission node for using command.

// Create permenant weed planters around the map for players to use for free.
Config.Commands.CreatePermenantPlanter = {}; // Do Not Touch
Config.Commands.CreatePermenantPlanter.Command = "CreatePermenantPlanter"; // Command Name
Config.Commands.CreatePermenantPlanter.Ace = "qbdev"; // Permission node for using command.

// Delete permenant weed planters
Config.Commands.DeletePermenantPlanter = {}; // Do Not Touch
Config.Commands.DeletePermenantPlanter.Command = "DeletePermenantPlanter"; // Command Name
Config.Commands.DeletePermenantPlanter.Ace = "qbdev"; // Permission node for using command.

// Create permenant weed tables around the map for players to use for free.
Config.Commands.CreatePermenantTable = {}; // Do Not Touch
Config.Commands.CreatePermenantTable.Command = "CreatePermenantTable"; // Command Name
Config.Commands.CreatePermenantTable.Ace = "qbdev"; // Permission node for using command.

// Delete permenant weed tables
Config.Commands.DeletePermenantTable = {}; // Do Not Touch
Config.Commands.DeletePermenantTable.Command = "DeletePermenantTable"; // Command Name
Config.Commands.DeletePermenantTable.Ace = "qbdev"; // Permission node for using command.

// Create permenant weed kitchens around the map for players to use for free.
Config.Commands.CreatePermenantKitchen = {}; // Do Not Touch
Config.Commands.CreatePermenantKitchen.Command = "CreatePermenantKitchen"; // Command Name
Config.Commands.CreatePermenantKitchen.Ace = "qbdev"; // Permission node for using command.

// Delete permenant weed kitchens
Config.Commands.DeletePermenantKitchen = {}; // Do Not Touch
Config.Commands.DeletePermenantKitchen.Command = "DeletePermenantKitchen"; // Command Name
Config.Commands.DeletePermenantKitchen.Ace = "qbdev"; // Permission node for using command.
```

## Server Exports

> There are no server exports for this resource

## Server Events

> There are no server events for this resource

## Client Exports

> There are no client exports for this resource

## Client Events

> There are no client events for this resource
