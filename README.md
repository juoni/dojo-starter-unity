# Integrate Unity with Dojo: A Quick Start Guide

This guide will walk you through the process of integrating Unity with Dojo.

## Initial Setup

The repository already contains the `dojo-starter` as a submodule. Feel free to remove it if you prefer.

**Prerequisites:** First and foremost, ensure that Dojo is installed on your system. If it isn't, you can easily get it set up with:

```console
curl -L https://install.dojoengine.org | bash
```

Followed by:

```console
dojoup
```

For an in-depth setup guide, consult the [Dojo book](https://book.dojoengine.org/getting-started/quick-start.html).

## Launch the Example

### Dojo Contract

After cloning the project, execute the following:

0. **init submodule**

```
git submodule update --init --recursive
```

1. **Terminal 1 - Katana**:

```console
cd dojo-starter && katana --disable-fee
```

2. **Terminal 2 - Contracts**:

```console
cd dojo-starter && sozo build && sozo migrate
```

### Unity

1. Go to Unity Hub and add the [unity](./unity) folder as a project.
2. In the Unity Editor, navigate to the `Starknet SDK -> Setup` to setup your game and do the following.
   - Select Dojo as your preferred game engine.
   - Enter `http://localhost:5050` as the RPC Node.
   - Enter the World Address and System Address gotten from `sozo migrate` as the World Address and System Address respectively.
3. Navigate to the `Assets -> Scenes -> Game` in the Project Hierarchy and open the `Game` scene.
4. In the Game Hierarchy, select the `PlayerCanvas -> Astronaut` object. In the Inspector, you should see a `Astronaut` component. Fill in the `Player Address` field with the address of the player and `Player key` with the from `Katana` terminal.

**Video Demo:**

[![Video Demo](https://youtu.be/sWkty7sdQ9o)](https://youtu.be/sWkty7sdQ9o)

### Making Requests to the Dojo Contract

The [`Astronaut.cs`](unity/Assets/Scripts/Astronaut.cs) contains starter code for reading and writing to the Dojo contract. You can use this as a reference to make requests to the Dojo contract.

```cs
void Execute(string model, string[] args)

// Examples

// Spawning a new Player
string[] spwanArgs = new string[] { };
Execute("spawn", spwanArgs);

// Moving the Player to the left
string[] moveArgs = new string[] { "1" };
Execute("move", moveArgs);
```
