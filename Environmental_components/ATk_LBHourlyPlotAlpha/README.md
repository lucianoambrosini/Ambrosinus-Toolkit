# ATk_LBHourlyPlotAlpha Component

## Overview

**ATk_LBHourlyPlotAlpha** is a Grasshopper component that extends Ladybug Tools' Hourly Plot functionality with advanced alpha highlighting capabilities. It creates colored plots of hourly environmental data collections with the ability to visually emphasize specific hours of the year by fading non-highlighted periods. This component is ideal for environmental analysis workflows where you need to draw attention to specific time periods while maintaining context of the full annual dataset.

<br>

<div align="center">
<img src="https://ambrosinus.altervista.org/blog/wp-content/uploads/2025/11/LBHourlyPlotAlpha_comp_01.png" width="25%" height="300%">
</div>

<br>

This component is part of the **Ambrosinus Toolkit** and builds upon the robust foundation of Ladybug Tools 1.8.0, maintaining full compatibility with Ladybug's data structures and visualization system.

<div align="center">
<img src="https://ambrosinus.altervista.org/blog/wp-content/uploads/2025/11/5_Cooling_Hourly_x2_5.jpg" width="70%" height="300%">
</div>

<br>
<br>
---

## Component Information

- **Name:** ATk_LBHourlyPlotAlpha
- **Nickname:** ATk_LBHourlyPlotAlpha
- **Category:** Ambrosinus → 7.Envi
- **Author:** Luciano Ambrosini
- **License:** AGPL-3.0-or-later
- **Version:** 1.0.0
- **Description:** Creates colored plots of hourly data collections with HOY alpha highlights for emphasizing specific time periods in environmental analysis.

---

## Key Features

### 🎨 Alpha Highlighting System
- **Fade non-highlighted hours** to emphasize specific time periods
- **Three intensity presets**: 'light' (60% opacity), 'mid' (30% opacity), 'strong' (10% opacity)
- **Precise HOY selection** for targeting specific hours of the year (1-8760)
- **Visual clarity** while maintaining full data context

### 📊 Enhanced Data Visualization
- **Multiple plot support** with automatic vertical stacking
- **Custom gap control** between plots or auto-calculation based on text height
- **2D and 3D chart modes** via z-dimension control
- **Reversible Y-axis** for different time orientation preferences

### 🔍 Detailed Information Output
- **Highlight curves** showing exact locations of selected HOYs
- **Detailed info strings** with date, time, and values for each highlighted hour
- **Value extraction** for further analysis and documentation

### 🔧 Full Ladybug Compatibility
- Works with **HourlyContinuousCollection** and **HourlyDiscontinuousCollection**
- Compatible with **LegendParameter** objects for legend customization
- Supports **AnalysisPeriod** filtering for time-based data subsets
- Accepts **conditional statements** for advanced data filtering

---

## How It Works

### Data Processing Flow

```
INPUT: Hourly Data Collection(s)
    ↓
[1] Validate and filter data
    - Check for valid Ladybug collections
    - Apply conditional statements (if any)
    - Apply analysis period filters (if any)
    ↓
[2] Calculate plot geometry
    - Determine grid dimensions (days × hours)
    - Apply user-defined or default dimensions
    - Calculate base points for multiple plots
    ↓
[3] Generate colored mesh
    - Map data values to colors via legend parameters
    - Apply alpha highlighting (if enabled)
    ↓
[4] Create visualization elements
    - Generate legend
    - Draw time borders (hours/months)
    - Create labels and title
    ↓
[5] Process HOY highlights (if specified)
    - Calculate cell positions for each HOY
    - Generate highlight polylines
    - Extract values and create info strings
    ↓
OUTPUT: Mesh, Legend, Labels, Highlights, Info
```

### Alpha Highlighting Mechanism

When alpha highlighting is enabled:

1. **Selected HOYs** are rendered at **full opacity** (100%)
2. **Non-selected hours** are faded based on the chosen preset:
   - **'light'**: 60% opacity (subtle fade)
   - **'mid'**: 30% opacity (moderate fade) - DEFAULT
   - **'strong'**: 10% opacity (dramatic fade)
3. **Color values** are preserved; only opacity changes
4. **Legend and borders** remain unaffected for consistent reference

---

## Inputs

| Input | Type | Access | Default | Optional | Description |
|-------|------|--------|---------|----------|-------------|
| **_data** | Generic | List | - | No | Ladybug HourlyContinuousCollection or HourlyDiscontinuousCollection. One or more data collections to plot. |
| **_base_pt_** | Point | Item | (0,0,0) | Yes | Base point for plot origin. Sets the starting position for the first plot. |
| **_x_dim_** | Number | Item | 1.0 | Yes | X dimension (width) of each mesh cell in model units. Represents one day. |
| **_y_dim_** | Number | Item | 4.0 | Yes | Y dimension (height) of each mesh cell in model units. Represents one hour. |
| **_z_dim_** | Number | Item | 0.0 | Yes | Z dimension for 3D chart elevation. Use 0 for flat 2D plots. |
| **reverse_y_** | Boolean | Item | False | Yes | Reverse Y-axis direction. Changes time flow from bottom-to-top to top-to-bottom. |
| **clock_24_** | Boolean | Item | False | Yes | Use 24-hour time format for labels. Default is 12-hour format (AM/PM). |
| **legend_par_** | Generic | List | - | Yes | Ladybug LegendParameter object(s) for customizing legend appearance, colors, and ranges. |
| **statement_** | String | Item | - | Yes | Conditional statement to filter data (e.g., 'a > 25' or 'a > 20 and a < 30'). |
| **period_** | Generic | Item | - | Yes | Ladybug AnalysisPeriod to filter data by specific time ranges (e.g., summer months only). |
| **highlight_hoys_** | Generic | List | - | Yes | List of Hour-of-Year values (1-8760) to highlight. Use with alpha_highlights_. |
| **alpha_highlights_** | Generic | Item | False | Yes | Enable alpha fade effect. Set to True to fade non-highlighted hours. |
| **alpha_preset_** | Generic | Item | 'mid' | Yes | Fade intensity preset: 'light' (60%), 'mid' (30%), or 'strong' (10%). |
| **gap_** | Number | Item | Auto | Yes | Vertical gap between multiple plots in model units. If not specified, auto-calculated based on text height. |

---

## Outputs

| Output | Type | Access | Description |
|--------|------|--------|-------------|
| **mesh** | Generic | Tree | Colored mesh(es) representing the hourly plot data. One mesh per data collection. |
| **legend** | Generic | Tree | Legend geometry with color scale and numerical labels. One legend per data collection. |
| **borders** | Generic | Tree | Lines and polylines showing time interval boundaries (hours and months). |
| **labels** | Generic | Tree | Text labels for hours and months positioned around the plot. |
| **title** | Generic | List | Title text object(s) with data collection information and metadata. |
| **vis_set** | Generic | Item | VisualizationSet arguments for advanced Rhino display control. |
| **highlight_crvs** | Generic | Tree/List | Polyline curves highlighting the selected HOY cells on the plot. |
| **sel_hoys_info** | Generic | Tree/List | Detailed information strings for each highlighted HOY (date, time, value). |
| **sel_hoys_values** | Generic | Tree/List | Numerical values of the data at the highlighted HOYs. |

---

## Usage Examples

### Example 1: Basic Hourly Plot (Standard Ladybug Functionality)

```
[EPW Weather Data] 
    ↓ 
[Dry Bulb Temperature Collection] ───→ [_data]
                                       [_base_pt_] = (0,0,0)
                                       [_x_dim_] = 1
                                       [_y_dim_] = 4
                                       ↓
                                   [ATk_LBHourlyPlotAlpha]
                                       ↓
                                   [mesh] → Full year temperature plot
                                   [legend] → Color scale with temp range
                                   [labels] → Month and hour labels
```

**Result:** Standard annual hourly plot showing temperature variations across 365 days and 24 hours.

---

### Example 2: Highlighting Summer Afternoon Peak Hours

**Scenario:** Emphasize hot afternoon hours (2 PM - 5 PM) during summer months (June-August).

```
Step 1: Calculate target HOYs
- June 15, 2 PM = HOY 4006
- June 15, 3 PM = HOY 4007
- June 15, 4 PM = HOY 4008
- June 15, 5 PM = HOY 4009
- ... (repeat for each day in summer)

Step 2: Connect to component
[Temperature Data] ───────────────→ [_data]
[List of HOYs] ──────────────────→ [highlight_hoys_]
[True] ──────────────────────────→ [alpha_highlights_]
[Text: "strong"] ────────────────→ [alpha_preset_]

Result:
- Peak hours visible at full opacity
- Other hours faded to 10% opacity
- Clear visual emphasis on critical periods
```

**Use Case:** Identify cooling load peaks, assess overheating risk, or communicate thermal discomfort periods to clients.

---

### Example 3: Comparing Multiple Datasets with Highlights

**Scenario:** Compare indoor vs outdoor temperature with occupancy hours highlighted.

```
[Outdoor Temperature] ─┐
[Indoor Temperature] ──┴───────→ [_data] (list of 2)
[Occupancy HOYs] ─────────────→ [highlight_hoys_] (e.g., 9 AM - 5 PM, weekdays)
[True] ───────────────────────→ [alpha_highlights_]
[Text: "mid"] ────────────────→ [alpha_preset_]
[Number: 10] ─────────────────→ [gap_] (custom spacing)

Outputs:
- mesh[0]: Outdoor temp plot
- mesh[1]: Indoor temp plot (below first)
- highlight_crvs[0]: Occupancy hours on outdoor plot
- highlight_crvs[1]: Occupancy hours on indoor plot
- sel_hoys_values[0]: Outdoor temps during occupancy
- sel_hoys_values[1]: Indoor temps during occupancy
```

**Analysis:** Directly compare indoor/outdoor conditions during occupied hours. Calculate average temperature differences during work hours.

---

### Example 4: Filtering with Analysis Period and Highlights

**Scenario:** Show only winter months (Dec-Feb) with nighttime hours emphasized.

```
[Annual Temperature Data] ────────────→ [_data]
[AnalysisPeriod: 12/1-2/28] ─────────→ [period_]
[Nighttime HOYs: 8 PM - 6 AM] ───────→ [highlight_hoys_]
[True] ───────────────────────────────→ [alpha_highlights_]
[Text: "light"] ──────────────────────→ [alpha_preset_] (subtle fade)

Result:
- Plot shows only winter months (Dec, Jan, Feb)
- Nighttime hours at full opacity
- Daytime hours at 60% opacity
- Easy identification of coldest nighttime periods
```

**Application:** Assess heating load during overnight periods, identify frost risk hours, or optimize nighttime setback strategies.

---

### Example 5: Advanced Filtering with Conditional Statement

**Scenario:** Highlight all hours where temperature exceeds 30°C for overheating analysis.

```
Method 1: Using Ladybug component to find HOYs
[Temperature Data] → [Filter by Conditional] → [HOYs > 30°C] → [highlight_hoys_]

Method 2: Using visual inspection
[Temperature Data] ─────────────────→ [_data]
[LegendParameter: range 28-32°C] ──→ [legend_par_]
[Empty] ────────────────────────────→ [highlight_hoys_] (none initially)

After visual inspection, add specific HOYs:
[Identified HOYs] ──────────────────→ [highlight_hoys_]
[True] ─────────────────────────────→ [alpha_highlights_]
[Text: "strong"] ───────────────────→ [alpha_preset_]

Result:
- Only overheating hours visible clearly
- Context hours heavily faded
- sel_hoys_info output provides exact dates/times
- sel_hoys_values output provides exact temperatures
```

---

## Alpha Preset Comparison

Visual comparison of the three fade intensity presets:

| Preset | Opacity | Visual Effect | Best Use Case |
|--------|---------|---------------|---------------|
| **light** | 60% | Subtle fade, maintains good context visibility | When you need to see patterns in non-highlighted hours |
| **mid** | 30% | Moderate fade, balanced emphasis | General use, good for presentations (DEFAULT) |
| **strong** | 10% | Dramatic fade, maximum contrast | When you want to almost hide non-highlighted hours |

### Visual Example (Conceptual)

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
LIGHT PRESET (60% opacity)
Full hours: █████ (highlighted)
Faded: ▓▓▓▓▓ (still clearly visible)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
MID PRESET (30% opacity) - DEFAULT
Full hours: █████ (highlighted)
Faded: ▒▒▒▒▒ (moderate visibility)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
STRONG PRESET (10% opacity)
Full hours: █████ (highlighted)
Faded: ░░░░░ (barely visible)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

---

## Understanding Hour-of-Year (HOY)

### What is HOY?

Hour-of-Year (HOY) is a continuous numbering system for hours in a year:
- **Range:** 1 to 8760 (or 8784 in leap years)
- **HOY 1** = January 1st, 12:00 AM - 1:00 AM
- **HOY 8760** = December 31st, 11:00 PM - 12:00 AM

### Calculating HOY

```
HOY = (Day_of_Year - 1) × 24 + Hour_of_Day + 1

Examples:
- January 1, 9 AM = (1-1) × 24 + 9 + 1 = HOY 10
- March 15, 3 PM (Day 74) = (74-1) × 24 + 15 + 1 = HOY 1768
- July 4, 6 PM (Day 185) = (185-1) × 24 + 18 + 1 = HOY 4435
- December 31, 11 PM (Day 365) = (365-1) × 24 + 23 + 1 = HOY 8760
```

### Getting HOY Values from Ladybug

Use Ladybug's analysis tools to extract HOYs based on conditions:

```
[Hourly Data] → [Filter by Conditional] → "a > threshold"
    ↓
[HOY Values Output] → Connect to highlight_hoys_
```

Or use the **Import EPW** and **Analysis Period** components to calculate HOYs for specific date/time ranges.

---

## Multiple Plots and Gap Control

### Automatic Gap Calculation (Default)

When `gap_` is not connected or set to 0, the component automatically calculates spacing based on:
- Text height from legend parameters
- Number of metadata lines in data collection
- Formula: `gap = text_height × (metadata_count + 6) × 1.5`

**Advantage:** Ensures titles and metadata never overlap between plots.

### Custom Gap Control

Connect a number to `gap_` to override automatic spacing:

```
[Number: 5] ───→ [gap_]  // Tight spacing
[Number: 15] ──→ [gap_]  // Medium spacing
[Number: 30] ──→ [gap_]  // Wide spacing
```

**Use Cases:**
- **Tight layouts** for documentation with limited page space
- **Wide spacing** when adding annotations between plots
- **Consistent spacing** across multiple charts for aligned presentation

---

## Technical Details

### Mesh Generation

The component creates colored meshes using Ladybug's visualization engine:

1. **Grid Structure:** 
   - X-axis: Days of year (365 or filtered range)
   - Y-axis: Hours per day (24 or filtered by analysis period)
   - Each cell = one hour of data

2. **Color Mapping:**
   - Values mapped to colors via LegendParameter
   - Colors assigned to mesh vertex colors
   - Alpha channel modified for non-highlighted cells (if enabled)

3. **Cell Dimensions:**
   - Width (`_x_dim_`): Typically 1 meter per day
   - Height (`_y_dim_`): Typically 4 meters per hour
   - Depth (`_z_dim_`): 0 for 2D, positive value for 3D extrusion

### HOY Highlight Calculation

For each highlighted HOY, the component:

1. Finds the corresponding datetime in the data collection
2. Calculates day index from analysis period start date
3. Calculates hour index from analysis period start hour
4. Accounts for reverse_y_ setting if enabled
5. Computes cell corner coordinates
6. Creates polyline highlighting the cell boundary

### Data Tree Structure (Multiple Collections)

When multiple data collections are provided:

```
mesh {0} → Collection 1 mesh
mesh {1} → Collection 2 mesh

legend {0;0} → Collection 1 legend geometry
legend {1;0} → Collection 2 legend geometry

highlight_crvs {0;0} → Collection 1, HOY 1 polyline
highlight_crvs {0;1} → Collection 1, HOY 2 polyline
highlight_crvs {1;0} → Collection 2, HOY 1 polyline
```

For single collections, highlight outputs are flattened (no tree structure).

---

## Compatibility and Requirements

### Required Software
- **Rhino 6.0** or later (Rhino 7/8 recommended)
- **Grasshopper** (included with Rhino)
- **Ladybug Tools 1.8.0** or later

### Dependencies
- Component relies on Ladybug's core libraries:
  - `ladybug_geometry` for geometric operations
  - `ladybug.datacollection` for data handling
  - `ladybug.graphic` for visualization
  - `ladybug.legend` for legend generation
  - `ladybug_rhino` for Rhino integration

### Data Type Requirements
- **Input data must be:** HourlyContinuousCollection or HourlyDiscontinuousCollection
- Data collections must contain hourly timestep data
- HOY values must be integers in range 1-8760

---

## Comparison with Standard Ladybug Hourly Plot

| Feature | Ladybug Hourly Plot | ATk_LBHourlyPlotAlpha |
|---------|---------------------|----------------------|
| Basic hourly plotting | ✓ | ✓ |
| Legend customization | ✓ | ✓ |
| Analysis period filtering | ✓ | ✓ |
| Conditional statements | ✓ | ✓ |
| Multiple data collections | ✓ | ✓ |
| **Alpha highlighting** | ✗ | ✓ |
| **HOY selection** | ✗ | ✓ |
| **Fade intensity presets** | ✗ | ✓ |
| **Highlight polylines output** | ✗ | ✓ |
| **Detailed HOY info strings** | ✗ | ✓ |
| **HOY value extraction** | ✗ | ✓ |
| **Custom gap control** | ✗ | ✓ |

---

## Practical Applications

### 1. **Overheating Analysis**
Highlight hours where temperature exceeds comfort thresholds to identify problematic periods for passive cooling strategies.

### 2. **Solar Availability Studies**
Emphasize peak solar radiation hours to optimize PV panel orientation and size.

### 3. **Occupancy Pattern Visualization**
Fade non-occupied hours to focus analysis on times when building performance matters most.

### 4. **Climate Zone Comparison**
Compare multiple locations with identical highlighted HOYs to see regional differences during specific conditions.

### 5. **Energy Peak Identification**
Highlight utility peak hours to assess cost implications and demand response opportunities.

### 6. **Natural Ventilation Potential**
Emphasize hours when outdoor conditions are within comfort range for natural ventilation.

### 7. **Daylighting Sufficiency**
Show hours when daylight levels meet minimum requirements for different space types.

### 8. **Client Presentations**
Create clear, visually striking graphics that draw attention to key findings without overwhelming with data.

---

## Best Practices

### ✓ Do's

- **Start with standard plot** before adding highlights to understand the full data context
- **Use 'mid' preset** as default; adjust only if needed for specific emphasis
- **Provide clear HOY lists** from upstream Ladybug analysis components
- **Match highlight HOYs** to your analysis questions (don't highlight randomly)
- **Export sel_hoys_info** to document exact highlighted conditions
- **Use custom gap** when creating multi-plot layouts for reports
- **Test alpha presets** to find the right balance for your audience

### ✗ Don'ts

- **Don't highlight too many hours** (defeats the purpose of emphasis)
- **Don't use 'strong' preset** unless you truly want to hide context
- **Don't ignore sel_hoys_values** output (useful for calculations)
- **Don't mix incompatible data types** (must be hourly collections)
- **Don't forget to connect highlight_hoys_** when alpha_highlights_ is True
- **Don't rely on visual inspection alone** for HOY selection (use Ladybug filters)

---

## Troubleshooting

### Component shows red error

**Problem:** Invalid input data type  
**Solution:** Ensure _data input receives HourlyContinuousCollection or HourlyDiscontinuousCollection from Ladybug components

---

### Highlights not showing

**Problem:** highlight_hoys_ connected but no curves output  
**Causes:**
- HOY values outside data collection range
- alpha_highlights_ not set to True
- HOYs not present in filtered data (check analysis period)

**Solution:** Verify HOYs exist in your data collection's time range. Check console for error messages.

---

### Alpha fade not visible

**Problem:** All cells appear same opacity  
**Causes:**
- alpha_highlights_ set to False
- No HOYs connected to highlight_hoys_
- alpha_preset_ string misspelled (must be exact: 'light', 'mid', or 'strong')

**Solution:** Enable alpha_highlights_ and ensure highlight_hoys_ contains valid values

---

### Multiple plots overlapping

**Problem:** Plots stack on top of each other  
**Causes:**
- gap_ set too small
- Negative gap_ value
- Very tall text height in legend parameters

**Solution:** Increase gap_ value or disconnect to use automatic spacing

---

### Wrong hours highlighted

**Problem:** Highlights appear in unexpected cells  
**Causes:**
- reverse_y_ setting doesn't match expectations
- Analysis period start time offset
- Incorrect HOY calculation

**Solution:** Check sel_hoys_info output to verify highlighted hours match intended times

---

### Memory or performance issues

**Problem:** Grasshopper slow or crashes with large datasets  
**Causes:**
- Many data collections (>10)
- High resolution data (sub-hourly)
- Thousands of highlighted HOYs

**Solution:** 
- Process collections in smaller batches
- Filter data to relevant time periods before plotting
- Reduce number of highlighted HOYs

---

## Advanced Tips

### Combining with Other Ladybug Components

```
[EPW] → [Import EPW] → [Dry Bulb Temp]
                           ↓
                    [Conditional Filter: "a > 28"] → [HOYs]
                           ↓                            ↓
                    [ATk_LBHourlyPlotAlpha] ←──────────┘
                        ↓
                    [highlight_crvs] → [BoundingBox] → [ViewCapture_Ztrigger]
```

**Result:** Automated capture of overheating periods with sequential zoom.

---

### Creating Custom Alpha Values

While the component provides three presets, you can manually adjust alpha by:
1. Extract mesh from component
2. Use custom script to modify vertex colors
3. Recolor specific faces based on sel_hoys_values

---

### Batch Processing Multiple Climate Files

```
[List of EPW paths] → [Import EPW (in loop)]
                           ↓
                    [Extract Temperature]
                           ↓
                    [ATk_LBHourlyPlotAlpha]
                           ↓
                    [Bake with layer names]
```

**Result:** Comparative climate analysis across multiple locations with consistent highlighting.

---

## Version History

### Version 1.0.0 (Current)

**Features:**
- Alpha highlighting with three intensity presets
- HOY selection and visualization
- Multiple plot support with custom gap control
- Highlight curve output
- Detailed HOY information strings
- HOY value extraction
- Full Ladybug Tools compatibility
- Compiled .ghpy format for source protection

**Based on:**
- Ladybug Tools 1.8.0 Hourly Plot component
- Original work © 2024 Ladybug Tools
- Hack & tweak © 2025 Luciano Ambrosini

---

## Author

**Luciano Ambrosini**

- Website: [lucianoambrosini.it](https://lucianoambrosini.it)
- Blog: [ambrosinus.altervista.org/blog/ambrosinus-toolkit](https://ambrosinus.altervista.org/blog/ambrosinus-toolkit/)
- Toolkit: Ambrosinus Toolkit
- Component Category: 7.Envi

---

## License

**AGPL-3.0-or-later**

This component extends Ladybug Tools, which is licensed under AGPL-3.0. This extension maintains the same license to comply with the original work's terms.

- Original work © 2024 Ladybug Tools
- Modifications © 2025 Luciano Ambrosini

---

## Credits

### Based On
This component is built upon and extends the excellent work of the **Ladybug Tools** team:
- Original Ladybug Hourly Plot component
- Ladybug core libraries for environmental analysis
- Ladybug geometry and visualization framework

### Modifications
- Alpha highlighting system with configurable fade intensities
- HOY selection and polyline generation
- Enhanced information outputs (sel_hoys_info, sel_hoys_values)
- Custom gap control for multiple plots
- Professional component packaging via GhPy compilation

---

## Support

For questions, bug reports, or feature requests:

1. **Documentation:** Check this README first
2. **Blog:** Visit [Ambrosinus DEV Log](https://ambrosinus.altervista.org/blog/ambrosinus-toolkit/)
3. **Ladybug Tools:** For base functionality questions, refer to [Ladybug Tools Discourse](https://discourse.ladybug.tools/)

---

## Installation

### Method 1: Yak Package Manager (Recommended)
```
Coming soon - Component will be available via Grasshopper's package manager
```

### Method 2: Manual Installation
1. Download the `.ghpy` file
2. In Grasshopper, go to `File → Special Folders → Components Folder`
3. Copy the `.ghpy` file into this folder
4. Restart Rhino/Grasshopper
5. Find component in `Ambrosinus → 7.Envi` category

---

## Related Components

### From Ambrosinus Toolkit
- **ViewCapture_Ztrigger** - Automated viewport zooming and screenshot capture
- Other environmental analysis tools (see toolkit documentation)

### From Ladybug Tools
- **Hourly Plot** - Original component (without alpha highlighting)
- **Import EPW** - Weather data import
- **Analysis Period** - Time range filtering
- **Conditional Filter** - Data filtering by conditions

---

## Future Development

Potential enhancements being considered:

- [ ] Custom alpha value input (beyond three presets)
- [ ] Multiple highlight groups with different colors
- [ ] Animation support for temporal highlighting
- [ ] Export highlight data as CSV
- [ ] Integration with legend parameter object for highlight color control
- [ ] Support for sub-hourly data with interpolated highlighting

---

## Changelog

### v1.0.0 - Initial Release
- Core alpha highlighting functionality
- Three intensity presets (light, mid, strong)
- HOY selection and visualization
- Multiple data collection support
- Custom gap control
- Comprehensive outputs (curves, info, values)
- Full Ladybug Tools compatibility
- Professional error handling and validation

---

*Last Updated: 2025*

---

## Quick Reference Card

```
┌─────────────────────────────────────────────────────────┐
│ ATk_LBHourlyPlotAlpha - Quick Reference                 │
├─────────────────────────────────────────────────────────┤
│ INPUTS                                                  │
│  _data           → Hourly data collection(s)            │
│  highlight_hoys_ → HOY numbers to emphasize (1-8760)    │
│  alpha_highlights_ → True to enable fade effect         │
│  alpha_preset_   → 'light'|'mid'|'strong'               │
│  gap_            → Space between multiple plots         │
│                                                         │
│ KEY OUTPUTS                                             │
│  mesh            → Colored plot visualization           │
│  highlight_crvs  → Polylines around selected HOYs       │
│  sel_hoys_info   → "HOY X: M/D HH:00 - Value: Y"        │
│  sel_hoys_values → Numerical values at highlighted HOYs │
│                                                         │
│ ALPHA PRESETS                                           │
│  light  = 60% opacity (subtle)                          │
│  mid    = 30% opacity (moderate) ← DEFAULT              │
│  strong = 10% opacity (dramatic)                        │
│                                                         │
│ HOY CALCULATION                                         │
│  HOY = (Day - 1) × 24 + Hour + 1                        │
│  Example: March 15, 3PM = HOY 1768                      │
└─────────────────────────────────────────────────────────┘
```
