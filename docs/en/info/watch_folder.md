# 🎬 PTN & Guessit Parser Documentation (preliminary version)

Documentation for **PTN** and **guessit** parsers for movies and TV shows, including support for RTL languages and Fallback to folder name.

---

## 1️⃣ PTN Parser

PTN parser supports parsing movie and TV show files with typical naming patterns.

### 🎥 Movies

| File Example | Parsed Data |
|-------------|-------------|
| `San Andreas 2015 720p WEB-DL x264 AAC-JYK.mkv` | Title: *San Andreas*, Year: 2015, Resolution: 720p, Video: x264, Audio: AAC, Group: JYK |
| `The Martian 2015 540p HDRip KORSUB x264 AAC2 0-FGT.mp4` | Title: *The Martian*, Year: 2015, Resolution: 540p, Video: x264, Audio: AAC2.0, Group: FGT |

### 📺 TV Shows

| File Example | Parsed Data |
|-------------|-------------|
| `friends.s02e01.720p.bluray-sujaidr.mkv` | Title: *Friends*, Season: 2, Episode: 1, Resolution: 720p, Format: bluray, Group: sujaidr |
| `Mr Robot S01E05 HDTV x264-KILLERS[ettv].mp4` | Title: *Mr Robot*, Season: 1, Episode: 5, Format: HDTV, Video: x264, Group: KILLERS |

---

## 2️⃣ guessit Parser

Guessit supports more complex file naming, including dot separators and multilingual titles.

### 🎥 Movies

| File Example | Parsed Data |
|-------------|-------------|
| `The.Matrix.1999.1080p.BluRay.x264.DTS-FGT.mkv` | Title: *The Matrix*, Year: 1999, Resolution: 1080p, Video: x264, Audio: DTS, Group: FGT |
| `Inception.2010.720p.BRRip.x264.AAC-ETRG.mkv` | Title: *Inception*, Year: 2010, Resolution: 720p, Video: x264, Audio: AAC, Group: ETRG |

### 📺 TV Shows

| File Example | Parsed Data |
|-------------|-------------|
| `Breaking.Bad.S03E07.720p.BluRay.x264-REWARD.mkv` | Title: *Breaking Bad*, Season: 3, Episode: 7, Resolution: 720p, Video: x264, Group: REWARD |
| `Game.of.Thrones.S05E09.1080p.WEB-DL.DD5.1.H.264-NTb.mkv` | Title: *Game of Thrones*, Season: 5, Episode: 9, Resolution: 1080p, Video: H.264, Audio: DD5.1, Group: NTb |

---

### 🔄 Fallback to Folder Name

If the file name does not contain the show title, enable **Fallback to Folder Name**:

| File Path Example | Parsed Data |
|-----------------|-------------|
| `/path/to/Show Name/S01E01 720p WEB-DL.mkv` | Title: *Show Name*, Season: 1, Episode: 1 |
| `/path/to/Show.Name/S01E01.720p.WEB-DL.mkv` | Title: *Show Name*, Season: 1, Episode: 1 |

#### 🗂 Season Folder Structure

If you want episodes sorted into season folders, the file name must contain the show title:

| File Path Example | Parsed Data |
|-----------------|-------------|
| `/path/to/Show Name/Season 01/Show Name S01E01 720p WEB-DL.mkv` | Title: *Show Name*, Season: 1, Episode: 1 |
| `/path/to/Show.Name/Season.01/Show.Name.S01E01.720p.WEB-DL.mkv` | Title: *Show Name*, Season: 1, Episode: 1 |

---

### 🌐 RTL Languages

For shows in RTL languages (Arabic, Hebrew, etc.):

- File name **should NOT contain the show title**  
- Enable **Fallback to Folder Name**  

| File Path Example | Parsed Data |
|-----------------|-------------|
| `/path/to/Show Name/S01E01 (year).mp4` | Title: *Show Name*, Season: 1, Episode: 1, Year: `year` |
| `/path/to/Show Name/Season 01/S01E01 (year).mp4` | Title: *Season 01*, Season: 1, Episode: 1, Year: `year` |

> ⚠️ Note: For RTL languages, the show title is taken only from the folder name.

---

### ✅ Summary

- **PTN Parser** — simple file names, local formats  
- **guessit Parser** — supports dot-separated names, multilingual titles, Fallback to folder name  
- **RTL Languages** — must use Fallback to folder name  
- **Season Folder Structure** — show title must be in the file name for correct sorting  

---

💡 **Tip:** Use consistent file and folder naming for accurate parsing and automatic season sorting.
