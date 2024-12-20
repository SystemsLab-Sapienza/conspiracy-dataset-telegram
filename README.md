# Conspiracy Resource and URL Datasets

This repository provides two datasets used in the USENIX Security 2025 paper:

**[The Conspiracy Money Machine: Uncovering Telegram's Conspiracy Channels and their Profit Model](https://arxiv.org/abs/2310.15977)**

If you use this dataset, or the findings from the paper, please cite:

```
@inproceedings{imperati2025conspiracy,
  title={The Conspiracy Money Machine: Uncovering Telegram's Conspiracy Channels and their Profit Model},
  author={Imperati, Vincenzo and La Morgia, Massimo and Mei, Alessandro and Mongardini, Alberto Maria and Sassi, Francesco},
  booktitle={34th USENIX Security Symposium (USENIX Security 25)},
  year={2025}
}
```

---

## Conspiracy Resource Dataset
The dataset is included in two files.
The `conspiracy_resource_dataset.csv` file contains the resources collected and their source. 
The `conspiracy_resource_dataset_supplementary.csv` file contains the identifiers of all videos shared within conspiracy-related YouTube channels. 
Indeed data we extracted from the sources consisted only of YouTube channel identifiers. We enhanced this dataset by extracting the IDs of all videos shared within these channels.

The `conspiracy_resource_dataset.csv` contains the following columns:

- **`resource`**: Contains the resource collected.
- **`platform`**: Specifies the platform targeted by the resource.  
- **`source_0`,`source_1`,`source_2`**: Each column contains a reference to the scientific paper or repository from which the resource was collected. 
Multiple columns are used because a resource can be mentioned in more than one scientific paper or repository. 

  
The `resource` field is interpreted differently based on the value of the `platform` field:


- **`youtube`**: Contains the identifier of a YouTube channel.  
    - Usage: If the field contains `UCKt4TYGQihKkrfLokfgWilg`, the channel can be accessed at: 
  www.youtube.com/channel/UCKt4TYGQihKkrfLokfgWilg
  
- **`reddit`**: Contains the identifier of a subreddit.  
  - Usage: If the field contains `UFOs`, the subreddit can be accessed at: www.reddit.com/r/UFOs
  
- **`8kun`**: Contains the identifier of an 8kun board.  
  - Usage: If the field contains `qresearch`, the board can be accessed at:
   www.8kun.top/qresearch
  
- **`voat`**: Contains the identifier of a Voat subverse.  
  - Usage: If the field contains `GreatAwakening`, the subverse can be accessed at: 
   www.voat.co/v/GreatAwakening 
  *(Note: Voat is currently shut down and can only be accessed through an archive:* https://searchvoat.co/v/*)*
  
- **`web`**: Contains the URL of a website.  
  - Usage: If the field contains `zerohedge.com`, the resource refers to the website: 
www.zerohedge.com

The `conspiracy_resource_dataset_supplementary.csv` file contains two columns:
- **`youtube_channel`**: Contains the identifier of a YouTube channel.
- **`youtube_video`**: Contains the identifier of a YouTube video we extracted from the corresponding Youtube channel.  
    - Usage:if the field contains the id: `j5T9xmWalGg`, the video can be accessed at: www.youtube.com/watch?v=j5T9xmWalGg


---
## Conspiracy URL Dataset
This dataset contains URLs shared within the channels included in [TGDataset](https://zenodo.org/records/7640712), the largest publicly available collection of Telegram channels.

To extract the URLs, we follow the above process, explained in detail in *Sec. 4.2* of the manuscript:

1. We collected all messages from Telegram channels included in the TGDataset.

2. We identified URLs shared in the collected messages and resolved any shortened URLs to their full form.

3. The extracted URLs were matched with resources in the **Conspiracy Resource Dataset**.  

At the end of this process, we identified a dataset of URLs that directly reference conspiracy resources and are actively shared on Telegram.
The dataset is contained in the ```conspiracy_url_dataset.csv``` file and contains three columns:

- **`URL`**: Indicates an URL extracted from a Telegram Channel  
- **`resource_main`**: Contains the  resource used to perform the match.  
- **`platform`**: Specifies the platform targeted by the resource.  

#### Notes on Data Extraction
 **Youtube** : We explored alternative platforms hosting YouTube videos that preserve their original identifiers (video and channel IDs). 
Specifically, we included URLs pointing to YouTube videos accessed through alternative frontends like [Invidious](https://invidious.io/) or [altCensored](https://altcensored.com/). 
Additionally, we considered matches found on platforms such as [Odysee](https://odysee.com/) and [Rumble](https://rumble.com/), which enable content creators to migrate videos directly from YouTube. 
Indeed, also in these cases, the migrated videos and channels retain their original YouTube identifiers.

**Voat**: Voat was shut down on December 25, 2020. Since then, the platform's content has been accessible only through an archive: http://searchvoat.co. For this reason, when searching for URLs matching Voat subverses, we consider both www.voat.co/v/ and https://searchvoat.co/v/.
