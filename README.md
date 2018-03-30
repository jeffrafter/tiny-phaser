# tiny-phaser

Test for phaser

Note this is an exact copy of https://github.com/photonstorm/phaser/blob/master/dist/phaser.js

It is experimental for use in Tiny.

See https://tttiny.com/@jeff/phaser-test/source

```
import _ from "https://services.tttiny.com/fetchLib/jeffrafter/tiny-phaser"

var config = {
  type: Phaser.AUTO,
  width: 300,
  height: 300,
  physics: {
    default: 'arcade',
    arcade: {
      gravity: { y: 200 }
    }
  },
  scene: {
    preload: preload,
    create: create
  }
};

var game = new Phaser.Game(config);

function preload ()
{
  this.load.setBaseURL('https://labs.phaser.io');

  this.load.image('sky', 'assets/skies/space3.png');
  this.load.image('logo', 'assets/sprites/phaser3-logo.png');
  this.load.image('red', 'assets/particles/red.png');
}

function create () {
  this.add.image(300, 300, 'sky');

  var particles = this.add.particles('red');

  var emitter = particles.createEmitter({
    speed: 100,
    scale: { start: 1, end: 0 },
    blendMode: 'ADD'
  });

  var logo = this.physics.add.image(400, 100, 'logo');

  logo.setVelocity(100, 200);
  logo.setBounce(1, 1);
  logo.setCollideWorldBounds(true);

  emitter.startFollow(logo);
}
```
