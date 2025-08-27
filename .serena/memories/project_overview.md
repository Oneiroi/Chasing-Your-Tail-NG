# Chasing Your Tail (CYT) - Project Overview

## Purpose
Chasing Your Tail (CYT) is a Wi-Fi probe request analyzer that monitors and tracks wireless devices by analyzing their probe requests. The system integrates with Kismet for packet capture and WiGLE API for SSID geolocation analysis, featuring advanced surveillance detection capabilities.

## Tech Stack
- **Primary Language**: Python 3.6+
- **Database**: SQLite (via Kismet wireless packet capture)
- **GUI Framework**: Tkinter
- **Key Dependencies**: 
  - requests>=2.28.0
  - cryptography>=40.0.0
- **External Systems**: 
  - Kismet wireless packet capture
  - WiGLE API for SSID geolocation
  - Google Earth (for KML visualization)

## Core Components
- **chasing_your_tail.py**: Core monitoring engine with real-time database queries
- **surveillance_analyzer.py**: GPS surveillance detection with automatic coordinate extraction
- **surveillance_detector.py**: Core persistence detection engine for suspicious device patterns  
- **cyt_gui.py**: Enhanced Tkinter GUI with surveillance analysis capabilities
- **gps_tracker.py**: GPS tracking with location clustering and KML generation
- **probe_analyzer.py**: Post-processing tool with WiGLE integration
- **Security modules**: secure_*.py files providing SQL injection prevention and encrypted credentials

## System Integration
- Kismet captures wireless frames and stores in SQLite database
- CYT queries database every 60 seconds for new devices/probes
- System maintains sliding time windows (5, 10, 15, 20 minutes) to track device persistence
- GPS coordinates are automatically extracted from Kismet Bluetooth GPS data
- Professional KML visualizations are generated for Google Earth analysis