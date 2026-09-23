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

* Architected and implemented gameplay systems in C# for combat, movement, and player abilities
* Built the multiplayer networking systems that synchronize players and gameplay state
* Implemented matchmaking, session control, and region-based deployment
* Integrated gameplay, networking, and UI into a released product
* Debugged latency and synchronization issues through playtesting and iteration

## Technical Breakdown

* **Server-authoritative gameplay:** The server owns core gameplay state and validates actions before replicating results to clients.
* **Client prediction:** Movement responds immediately to local input instead of waiting for a server round trip.
* **State reconciliation:** Clients correct predicted state when it differs from the server’s authoritative result.
* **Lag compensation:** Historical state rewind lets the server evaluate shots against player positions at the time they were fired.
* **Modular gameplay systems:** Combat, movement, and abilities were designed as distinct systems that could be developed and iterated on independently.
* **Network traffic optimization:** Gameplay state was synchronized for matches of up to 40 players while the game supported 300 concurrent users.

## Key Engineering Challenges

**Accurate Hits at High Latency**
At 200 ms or higher ping, evaluating shots against current positions produced inconsistent results. I implemented server-side rewind so hit detection could account for network delay.

**Responsive Movement with Server Authority**
Waiting for the server before applying input made controls feel delayed. I combined local prediction with server reconciliation to preserve responsiveness and correct state divergence.

**Trusting an Untrusted Client**
Players can modify client code. I kept core gameplay decisions on the server and replicated validated results to clients, reducing the impact of manipulated client data.

**Scaling Real-Time Sessions**
A 40-player FPS generates frequent movement and combat updates. I worked on network traffic and synchronization behavior to support full matches across five regions.

## Scale

* 1M+ downloads on Steam
* 300 concurrent players
* 40-player real-time matches
* Deployed across five regions

## DEMO

The original servers are no longer active. To play, use the modded demo, which runs through a different Steam game setup.

1. Download and install the demo: https://drive.google.com/file/d/1UoxqCMN4VNJ0DlIm-IpZ52WMNxId3A6h/view?usp=drive_link
2. Open Steam and download Cube Racer: https://store.steampowered.com/app/705210/Cube_Racer/
3. Open the launcher and select a Scram version to play.
