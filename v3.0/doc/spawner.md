# ComponentSpawner

A way to auto generate objects

Component Spawner are simple use components that allow you to spawn entities between a defined time.

The Component Spawner can be set using the following parameters.

```dart
    objectsBuilder: {
        'spawn': (properties) => ComponentSpawner(
            position: properties.position,
            area: properties.area,
            interval: 500,
            builder: (position) {
                return PotionLife(position, 1, size: Vector2.all(10));
            },
        ),
    },
```

Check a [example](https://github.com/RafaelBarbosatec/bonfire/blob/v3.0.0/example/lib/simple_example/simple_example_game.dart).

you can also define "onlyVisible" and "spawCondition" properties. 

The onlyVisible property only generate objects when it's visible on screen, for default this property are true, but if you want, you can define it to false.

"spawnCondition" property allow you to only generate objects or entities when the spawn condition are satisfied. For exemple: spawn potions until a max of 10, when the player collect one, potions can spawn again

```dart
    objectsBuilder: {
        'spawn': (properties) => ComponentSpawner(
            position: properties.position,
            area: properties.area,
            interval: 500,
            builder: (position) {
                return PotionLife(position, 1, size: Vector2.all(10));
            },
            spawCondition: (game) {
                return game.query<PotionLife>().length < 10;
            },
            spawCondition: (game) {
                return game.query<PotionLife>().length < 10;
            },
            onlyVisible: false,
        ),
    },
```

> <small>This is [Component Spawner](https://github.com/RafaelBarbosatec/bonfire/blob/v3.0.0/lib/util/component_spawner.dart) source code</small>
