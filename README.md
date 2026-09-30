
# Adopt a Satellite

> Decommissioned, Not Forgotten.

**Team Name:** Team Tiny Spark  
**Challenge Category:** Abandoned, Not Forgotten  
**Event:** NASA Space Apps Challenge 2026  

---

## Executive Summary

"Adopt a Satellite" is an interactive, empathy-driven web application designed to connect students and young space enthusiasts with human-made satellites currently orbiting Earth in silence. By combining real-time orbital telemetry data with a gamified digital adoption framework, the platform transforms inactive space debris into educational instruments and digital "celestial pen pals."

---

## Problem Statement

Over 11,000 tons of artificial objects currently orbit Earth. While active satellites drive modern telecommunications, thousands of historical, decommissioned satellites remain in high-altitude graveyard orbits, viewed strictly as space debris. Furthermore, traditional STEM education often treats orbital mechanics as abstract and distant. Young learners lack emotional connection and intuitive tools to explore the human history drifting through the cosmos.

---

## Solution

"Adopt a Satellite" bridges science and empathy. Users select a historic, silent satellite (such as Vanguard 1, Explorer 1, or Sputnik 1), track its live position using real-time Two-Line Element (TLE) data, and build digital "Time Capsules" containing notes, drawings, or audio messages. The app simulates a dynamic radio reply using environmental telemetry metrics and exports a shareable Space Postcard and official Adoption Certificate—all executed through client-side browser processing.

---

## Core Features

1. **Adoption Portal:** Browse, filter, and adopt historic decommissioned satellites with custom naming and avatar assignment.
2. **Real-Time Telemetry Tracker:** Interactive visual tracking displaying latitude, longitude, altitude, velocity, and 2D orbital projections using satellite.js.
3. **Silence Counter:** High-precision tracker calculating the exact duration (years, days, hours, seconds) since the satellite's final transmitted signal.
4. **Ghost Signal Audio FX:** Web Audio API synth module reproducing synthetic radio pings and Morse code telemetry effects upon connection.
5. **Time-Capsule Builder:** Interactive canvas for writing notes, creating drawings, or attaching voice recordings.
6. **Transmission Visualizer:** Orbital trajectory animation simulating signal beams during calculated overhead passes.
7. **Dynamic Radio Reply Engine:** Automated response system generating context-aware radio replies based on real telemetry data (altitude, solar angle, atmospheric tier).
8. **Space Postcard Generator:** Client-side canvas export tool (html2canvas) formatting user art and satellite replies into shareable PNG postcards.
9. **Rescue or Remember Module:** Educational interface presenting historical debris metrics, decay estimates, and orbital sustainability insights.
10. **Memory Orbit (Community Map):** Visual compilation showcase displaying anonymized user time-capsules pinned to orbital coordinates.
11. **Digital Passport & Certificate:** Progress tracker awarding badges ("Historian", "Time Capsule", "Signal Tuner") and downloadable NASA Space Apps Adoption Certificates.

---

## Technical Architecture & Data Flow

The application is built on a zero-backend, client-side execution framework to ensure low latency and offline usability.