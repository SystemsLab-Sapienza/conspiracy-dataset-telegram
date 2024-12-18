# Conspiracy Resource and URL Datasets

This repository provides two datasets used in the USENIX Security 2025 paper:

**[The Conspiracy Money Machine: Uncovering Telegram's Conspiracy Channels and their Profit Model](https://arxiv.org/abs/2310.15977)**

Below, we detail the structure of each dataset. For additional information on data collection and analysis, please refer to *Section 4.1* of the manuscript.

---

## Conspiracy Resource Dataset
This dataset is a collection of conspiracy-related resources extracted from an extensive review of the scientific works
about conspiracy theories.

The dataset is included in the `conspiracy_resource_dataset.csv` file, which contains the following columns:

- **`source`**: Indicates the scientific paper or repository from which the resource was collected.  
- **`platform`**: Specifies the platform targeted by the resource.  
- **`resource_main`**: Contains the main resource collected.  
- **`resource_supplementary`**: (Optional) Provides additional data we extracted starting from the main resources.


The `resource_main` field is interpreted differently based on the value of the `platform` field:

- **`youtube`**: Contains the identifier of a YouTube channel.  
    - Usage: If the field contains `UCKt4TYGQihKkrfLokfgWilg`, the channel can be accessed at: 
  `www.youtube.com/channel/UCKt4TYGQihKkrfLokfgWilg`
  
- **`reddit`**: Contains the identifier of a subreddit.  
  - Usage: If the field contains `UFOs`, the subreddit can be accessed at: 
  `www.reddit.com/r/UFOs`
  
- **`8kun`**: Contains the identifier of an 8kun board.  
  - Usage: If the field contains `qresearch`, the board can be accessed at:
  `www.8kun.top/qresearch`
  
- **`voat`**: Contains the identifier of a Voat subverse.  
  - Usage: If the field contains `GreatAwakening`, the subverse can be accessed at: 
  `www.voat.co/v/GreatAwakening` 
  *(Note: Voat is currently shut down.)*
  
- **`web`**: Contains the URL of a website.  
  - Usage: If the field contains `zerohedge.com`, the resource refers to the website: 
  `www.zerohedge.com`

The scientific work we analyzed contained only a list of conspiracy-related YouTube channels. We enriched this data by extracting the identifiers of all videos shared within these channels.
The `resource_supplementary` field contains the identifiers of these YouTube videos. In this case, if the field contains the id: `j5T9xmWalGg`, the video can be accessed at: www.youtube.com/watch?v=j5T9xmWalGg

## Conspiracy URL Dataset

The dataset is contained in the ```conspiracy_url_dataset.csv``` file.