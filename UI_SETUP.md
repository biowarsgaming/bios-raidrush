# UI Setup Guide for bios-raidrush

This guide helps you set up a basic UI for your tower defense game in Unity.

---

## 1. Core UI Elements

- **Tower Selection Panel**: Displays available towers (with icons, cost, and name).
- **Info Panel**: Shows player gold, lives, current wave.
- **Selected Tower Panel**: Displays stats/upgrades for the currently selected tower.
- **Controls Panel**: Start, pause, speed, and restart buttons.
- **Notification Panel**: Shows popups for events (e.g., “Not enough gold”, “Tower upgraded”).

---

## 2. Example Unity Hierarchy

```
Canvas
├── TowerPanel
│   ├── TowerButton (repeat for each tower)
├── InfoPanel
│   ├── GoldText
│   ├── LivesText
│   ├── WaveText
├── SelectedTowerPanel
│   ├── StatsText
│   ├── UpgradeButton
│   ├── FusionButton
├── ControlsPanel
│   ├── StartButton
│   ├── PauseButton
│   ├── SpeedButton
├── NotificationPanel
│   ├── NotificationText
```

---

## 3. Sample UI Script: Tower Selection

```csharp
using UnityEngine;
using UnityEngine.UI;

public class TowerPanelController : MonoBehaviour
{
    public Transform towerButtonContainer;
    public GameObject towerButtonPrefab;
    public TowerManager towerManager;

    void Start()
    {
        foreach (var towerType in towerManager.availableTowers)
        {
            var btnObj = Instantiate(towerButtonPrefab, towerButtonContainer);
            var btn = btnObj.GetComponent<Button>();
            btn.GetComponentInChildren<Text>().text = towerType.towerName;
            btn.image.sprite = towerType.icon;
            btn.onClick.AddListener(() => towerManager.SelectTower(towerType));
        }
    }
}
```

---

## 4. Connecting UI to Game Logic

- Reference your managers (`TowerManager`, `EnemyManager`, `WaveManager`) in UI scripts.
- Use UnityEvents, or update UI elements from game manager scripts.
- Example: Update gold/lives text when player earns or spends gold.

---

## 5. Advanced Features (Optional)

- **Tooltips**: Show tower/enemy info on hover.
- **Drag-and-drop**: Place towers by dragging from the panel onto the map.
- **Animated popups**: Use Unity Animator for smooth notification transitions.
- **Shop/Inventory**: Expand TowerPanel into a shop UI.

---

You can copy/paste or expand these elements as needed.  
If you want a full set of UI scripts, prefab samples, or integration examples, just ask!