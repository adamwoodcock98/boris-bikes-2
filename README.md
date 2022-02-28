Airport Challenge
=================

To deliver a system that emulates the docking system, bikes and infrastructure (repair staff, etc.) required to make this function in the real world.

```
                                         $"   *.      
              d$$$$$$$P"                  $    J
                  ^$.                     4r  "
                  d"b                    .db
                 P   $                  e" $
        ..ec.. ."     *.              zP   $.zec..
    .^        3*b.     *.           .P" .@"4F      "4
  ."         d"  ^b.    *c        .$"  d"   $         %
 /          P      $.    "c      d"   @     3r         3
4        .eE........$r===e$$$$eeP    J       *..        b
$       $$$$$       $   4$$$$$$$     F       d$$$.      4
$       $$$$$       $   4$$$$$$$     L       *$$$"      4
4         "      ""3P ===$$$$$$"     3                  P
 *                 $       """        b                J
  ".             .P                    %.             @
    %.         z*"                      ^%.        .r"
       "*==*""                             ^"*==*""   
```

Getting started
-------

1. Fork this repo, and clone to your local machine
2. Run the command `gem install bundler` (if you don't have bundler already)
3. When the installation completes, run `bundle`

Instructions
---------

### Creating a new docking station

To instantiate a new docking station object, navigate to the project directory and start a new IRB requiring the `docking_station.rb` file:
```bash
adamwoodcock@Adams-MacBook-Pro boris-bikes-2 % irb -r ./lib/docking_station.rb
3.0.0 :001 > docking_station = DockingStation.new
 => #<DockingStation:0x00007faa3b0f6418 @rack=[], @capacity=20> 
```
This creates a new docking station object, initialising with a default capacity of 20 bikes.

### Docking a bike

To dock a bike at the docking station, you will need to create a bike object.
```bash
adamwoodcock@Adams-MacBook-Pro boris-bikes-2 % irb -r ./lib/docking_station.rb
3.0.0 :001 > bike = Bike.new
 => #<Bike:0x00007f81388d1dd0> 
3.0.0 :002 > docking_station = DockingStation.new
 => #<DockingStation:0x00007f81388e99a8 @rack=[], @capacity=20> 
3.0.0 :003 > docking_station.dock(bike)
 => [#<Bike:0x00007f81388d1dd0>] 
```

#### Viewing stored bikes
You can use the `bikes` getter method to view the bikes currently stored at the docking station.
```bash
adamwoodcock@Adams-MacBook-Pro boris-bikes-2 % irb -r ./lib/docking_station.rb
3.0.0 :001 > docking_station = DockingStation.new
 => #<DockingStation:0x00007fd055926ff8 @rack=[], @capacity=20> 
3.0.0 :002 > 5.times { docking_station.dock(Bike.new) }
 => 5 
3.0.0 :003 > docking_station.bikes
 => [#<Bike:0x00007fd0568d4f90>, #<Bike:0x00007fd0568d4ef0>, #<Bike:0x00007fd0568d4ec8>, #<Bike:0x00007fd0568d4ea0>, #<Bike:0x00007fd0568d4e78>] 
```

### Releasing bikes from the dock

You can use the `release_bike` method to release a bike from the station.
```bash
adamwoodcock@Adams-MacBook-Pro boris-bikes-2 % irb -r ./lib/docking_station.rb
3.0.0 :001 > docking_station = DockingStation.new
 => #<DockingStation:0x00007faa7c9190c8 @rack=[], @capacity=20> 
3.0.0 :002 > docking_station.dock(Bike.new)
 => [#<Bike:0x00007faa7c04c788>] 
3.0.0 :003 > docking_station.release_bike
 => #<Bike:0x00007faa7c04c788> 
3.0.0 :004 > docking_station.bikes
 => [] 
```

### Marking a bike as broken

You can use the `report broken` method to report bikes as broken when docking them.
```bash
adamwoodcock@Adams-MacBook-Pro boris-bikes-2 % irb -r ./lib/docking_station.rb
3.0.0 :001 > docking_station = DockingStation.new
 => #<DockingStation:0x00007ff66c9391e8 @rack=[], @capacity=20> 
3.0.0 :002 > bike = Bike.new
 => #<Bike:0x00007ff66c91f428> 
3.0.0 :003 > bike.report_broken
 => true 
3.0.0 :004 > docking_station.dock(bike)
 => [#<Bike:0x00007ff66c91f428 @broken=true>] 
```

### Coverage
There are various methods in place to ensure the correct use of docking stations. Certain things will be restricted:
* You will not be able to release a broken bike
* You will not be able to release a bike from an empty docking station
* You will not be able to dock a bike to a full docking station

Testing
-------

The program contains a series of tests using Rspec (this library should be installed if the steps above were followed)

To run all tests across all class files, do the following:

```bash
cd Navigate/to/project/directory

rspec
```

To run tests for a specific class file, do the following:

```bash
cd Navigate/to/project/directory

rspec spec/docking_station_spec.rb
# or
rspec spec/bike_spec.rb
```
Tests include cases such as full docking stations, broken bikes and more.

Task
-----

Welcome to being a developer
Let's go back several years, to the days when there were no Boris Bikes. Imagine that you're a junior developer (that was easy). Transport for London, the body responsible for delivery of a new bike system, come to you with a plan: a network of docking stations and bikes that anyone can use. They want you to build a program that will emulate all the docking stations, bikes, and infrastructure required to make their dream a reality.
