# RAGE Multiplayer Polygons API

I recently needed a polygons library like this for my gamemode to define some companies, houses, gangzones and other kind of establishments boundaries, so I decided to create this resource.

Basically you'll be able to create any kind of colshape you want, without worring about combining colshapes to fit your needs, you can just define the points and the height of the shape and it'll be created easily!

## Where should I use this though?

You can use this plugin for setting boundaries for houses to move furnitures, for companies to accomplish the job, for mountains in hunting animals scripts and anything else your creativity takes you, just use it!

## API Functions

```ts
/* Creates a new polygon and return it's instance */
mp.polygons.add(vertices: Vector3Mp[], height: number, options = { visible: false, lineColorRGBA: [255,255,255,255], dimension: 0 }): Polygon

/* Removes a polygon */
mp.polygons.remove(polygon: Polygon): void

/* Check if a polygon exists */
mp.polygons.exists(polygon: Polygon): boolean

/* Check if a position is contained within a given polygon */
mp.polygons.isPositionWithinPolygon(position: Vector3Mp, polygon: Polygon): boolean

/* Examples */

// Creating a new polygon
const polygon = mp.polygons.add([new mp.Vector3(10, 10, 5), new mp.Vector3(15, 15, 5), new mp.vector3(5, 5, 5)], 10, { visible: false, lineColorRGBA: [255,255,255,255], dimension: 0 });

// Set the polygon lines visible 
polygon.visible = true;

// Modifying a polygon height
polygon.height = 100;

// Modifying a polygon color (RGBA)
polygon.lineColorRGBA = [255, 155, 0, 255];

// Modifying a polygon dimension
polygon.dimension = 30;

/* Events*/

// Event called when player enter a polygon (clientside)

mp.events.add('playerEnterPolygon', (polygon) => mp.gui.chat.push(`You entered the polygon ${polygon.id}!`));

// Event called when the local player leaves a polygon (clientside)

mp.events.add('playerLeavePolygon', (polygon) => mp.gui.chat.push(`You left the polygon ${polygon.id}.`));
```

## Releasement

You can check the [official releasement thread](https://rage.mp/files/file/343-js-clientside-polygons-api-dynamic-colshapes/) at RAGE Multiplayer's forums.