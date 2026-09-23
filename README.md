# Scram: Multiplayer PvP Shooter made in Unity

<p align="center">
  <a href="https://www.youtube.com/watch?v=ZZ6y3P8Cp5E"><strong>▶Watch Video Demo</strong></a>
</p>
<p align="center">
  <a href="https://www.youtube.com/watch?v=ZZ6y3P8Cp5E">
    <img src="https://github.com/user-attachments/assets/7d8942a4-7338-4dc8-9dcb-7238e8f5eb41"
         alt="Scram 2 Gameplay Demo"
         width="500" />
  </a>
</p>

<p align="center">
Scram is a 40-player multiplayer FPS built in Unity with C# and Photon Bolt. I led its development from prototype through release, engineering the gameplay and networking systems behind combat, movement, matchmaking, and real-time player synchronization across five regions.
</p>

<p align="center">
  <a href="https://github.com/user-attachments/assets/98b9b0b7-b270-439b-91e7-178c4f599ce5"><img src="https://github.com/user-attachments/assets/98b9b0b7-b270-439b-91e7-178c4f599ce5" width="45%"/></a>
  <a href="https://github.com/user-attachments/assets/30580ac7-cb9b-4c85-920d-c5a49a03b9ba"><img src="https://github.com/user-attachments/assets/30580ac7-cb9b-4c85-920d-c5a49a03b9ba" width="45%"/></a>
</p>
<p align="center">
  <a href="https://github.com/user-attachments/assets/5222afed-3953-40b7-b8ff-bffe38f7b3c6"><img src="https://github.com/user-attachments/assets/5222afed-3953-40b7-b8ff-bffe38f7b3c6" width="45%"/></a>
  <a href="https://github.com/user-attachments/assets/1b5b6a3d-fe39-4b05-8145-044b7aa6d7bb"><img src="https://github.com/user-attachments/assets/1b5b6a3d-fe39-4b05-8145-044b7aa6d7bb" width="45%"/></a>
</p>
<p align="center">
  <a href="https://github.com/user-attachments/assets/53d47753-849f-4a8d-b892-a4e80f50e4af"><img src="https://github.com/user-attachments/assets/53d47753-849f-4a8d-b892-a4e80f50e4af" width="45%"/></a>
  <a href="https://github.com/user-attachments/assets/72012c6e-c6b2-497a-b555-bc76c15cb961"><img src="https://github.com/user-attachments/assets/72012c6e-c6b2-497a-b555-bc76c15cb961" width="45%"/></a>
</p>
<p align="center">
  <img src="https://github.com/user-attachments/assets/d4afa750-696b-4515-b95b-75799c8e11e0" width="400"/>
  <img src="https://github.com/user-attachments/assets/cd206fc0-2a50-4841-9a85-e766eea5b664" width="400"/>
</p>

## My Role
* Designed and implemented C# gameplay systems for player locomotion, combat, and abilities within Unity.
* Engineered multiplayer state synchronization and client/server interactions using Photon Bolt.
* Implemented matchmaking, session lifecycle management, and support for deployment across five regions.
* Integrated gameplay, networking, and UI systems into a production multiplayer release.
* Diagnosed and resolved latency, hit registration, and state synchronization issues through multiplayer playtesting.

## Technical Breakdown
* **Server-authoritative simulation:** Core gameplay decisions are validated on the server, which maintains authoritative state and replicates results to connected clients.
* **Client-side prediction:** Local movement input is applied immediately on the client to avoid waiting for network round trips before the player receives feedback.
* **Server reconciliation:** Predicted client state is compared with authoritative server state and corrected when the two diverge.
* **Lag-compensated hit detection:** The server uses historical player state to evaluate shots against positions corresponding to when the firing client took the shot.
* **Modular C# gameplay architecture:** Combat, movement, and player abilities are implemented as separate systems, allowing their behavior to be developed and adjusted independently.
* **Multiplayer traffic management:** State synchronization was designed to support real-time combat in 40-player matches, with the game reaching 300 concurrent players.

## Key Engineering Challenges
**Hit registration under latency:** At 200 ms or higher ping, resolving shots against current server positions could produce results that differed from what the firing player saw. I implemented server-side historical rewind to evaluate hits using earlier player state.

**Responsive movement under server authority:** Waiting for authoritative updates introduced perceptible input latency. I implemented client-side prediction for immediate movement feedback and reconciliation to correct deviations from server state.

**Client trust boundaries:** Because client code can be modified, client-reported gameplay outcomes cannot be treated as authoritative. Core gameplay decisions are validated server-side before the resulting state is replicated to other players.

**Real-time synchronization at match scale:** A 40-player session requires frequent movement and combat updates across clients with different network conditions. I worked on synchronization and network traffic behavior to maintain playable sessions across five regions.

## Scale
* 1M+ Steam downloads
* 300 concurrent players
* 40 players per real-time match
* Deployment across five regions

## DEMO
The original servers are no longer active. To play, use the modded demo, which runs through a different Steam game setup.

1. Download and install the demo: https://drive.google.com/file/d/1UoxqCMN4VNJ0DlIm-IpZ52WMNxId3A6h/view?usp=drive_link
2. Open Steam and download Cube Racer: https://store.steampowered.com/app/705210/Cube_Racer/
3. Open the launcher and select a Scram version to play.
