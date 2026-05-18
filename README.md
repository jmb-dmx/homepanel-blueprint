# Entrance Panel ESPHome Dashboard

This repository contains the configuration files for an ESPHome-based smart home dashboard designed for the Waveshare ESP32-S3-Touch-LCD-7 screen. It integrates seamlessly with Home Assistant via a dedicated Blueprint.

## Architecture

The project uses a **Push Architecture**. The ESPHome device does not poll Home Assistant directly for dynamic data (like weather or media). Instead, the Home Assistant Blueprint listens for state changes and actively pushes the updated data to the ESPHome screen via custom API services. This ensures instant updates and allows you to configure everything (entities, buttons, QR codes) centrally from the Home Assistant UI without needing to recompile the ESPHome firmware.

## Files

- `entrance-panel-blueprint.yaml`: The ESPHome firmware configuration file.
- `entrance_panel_ha_blueprint.yaml`: The Home Assistant Blueprint used to configure and drive the screen.

## Installation

### 1. ESPHome Firmware
1. Copy `entrance-panel-blueprint.yaml` to your Home Assistant's `esphome/` directory.
2. Compile and install the firmware to your Waveshare ESP32-S3-Touch-LCD-7 screen using the ESPHome add-on.

### 2. Home Assistant Blueprint
1. Copy `entrance_panel_ha_blueprint.yaml` to your Home Assistant's `blueprints/automation/` directory (you may create a subfolder like `esphome_panels/`).
2. Go to **Settings > Automations & Scenes > Blueprints** and reload your blueprints.
3. Create a new automation from the "Entrance Panel Configuration" blueprint.
4. Fill in the required inputs:
   - **Panel Device:** Select the ESPHome device.
   - **ESPHome Node Name:** The internal name (default is `entrance_panel`).
   - **Weather & Media:** Select your weather entity, outdoor temperature sensor, and up to 3 media players.
   - **Guest Wi-Fi QR:** Enter your Wi-Fi credentials in the required format (e.g., `WIFI:S:MyNetwork;T:WPA;P:MyPassword;;`).
   - **Buttons 1-8:** Configure the entities, names, icons, and action types (light, script, or media_player) for the main dashboard buttons.
5. Save and enable the automation. The screen will automatically sync its configuration on the next boot or immediately upon state changes.

---

# Tableau de Bord ESPHome (Écran d'Entrée)

Ce dépôt contient les fichiers de configuration pour un tableau de bord domotique basé sur ESPHome, conçu pour l'écran Waveshare ESP32-S3-Touch-LCD-7. Il s'intègre parfaitement à Home Assistant via un Blueprint dédié.

## Architecture

Le projet utilise une **Architecture Push**. L'appareil ESPHome n'interroge pas directement Home Assistant pour les données dynamiques (comme la météo ou les médias). C'est le Blueprint Home Assistant qui écoute les changements d'état et pousse activement les nouvelles données vers l'écran ESPHome via des services API personnalisés. Cela garantit des mises à jour instantanées et vous permet de tout configurer (entités, boutons, codes QR) de manière centralisée depuis l'interface Home Assistant sans avoir à recompiler le firmware ESPHome.

## Fichiers

- `entrance-panel-blueprint.yaml` : Le fichier de configuration du firmware ESPHome.
- `entrance_panel_ha_blueprint.yaml` : Le Blueprint Home Assistant utilisé pour configurer et piloter l'écran.

## Installation

### 1. Firmware ESPHome
1. Copiez `entrance-panel-blueprint.yaml` dans le répertoire `esphome/` de votre Home Assistant.
2. Compilez et installez le firmware sur votre écran Waveshare ESP32-S3-Touch-LCD-7 en utilisant l'add-on ESPHome.

### 2. Blueprint Home Assistant
1. Copiez `entrance_panel_ha_blueprint.yaml` dans le répertoire `blueprints/automation/` de votre Home Assistant (vous pouvez créer un sous-dossier comme `esphome_panels/`).
2. Allez dans **Paramètres > Automatisations et Scènes > Blueprints** et rechargez vos blueprints.
3. Créez une nouvelle automatisation à partir du blueprint "Entrance Panel Configuration".
4. Remplissez les champs requis :
   - **Panel Device :** Sélectionnez l'appareil ESPHome.
   - **ESPHome Node Name :** Le nom interne (par défaut `entrance_panel`).
   - **Météo & Médias :** Sélectionnez votre entité météo, votre capteur de température extérieure et jusqu'à 3 lecteurs multimédias.
   - **QR Code Wi-Fi Invités :** Entrez vos identifiants Wi-Fi dans le format requis (ex: `WIFI:S:MonReseau;T:WPA;P:MonMotDePasse;;`).
   - **Boutons 1-8 :** Configurez les entités, noms, icônes et types d'action (lumière, script ou lecteur média) pour les boutons principaux du tableau de bord.
5. Sauvegardez et activez l'automatisation. L'écran synchronisera automatiquement sa configuration au prochain démarrage ou immédiatement lors de changements d'état.
