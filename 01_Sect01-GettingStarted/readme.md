# Section 1 - Getting Started 

## Objectives
- [ ] Install `anaconda`
- [ ] Install `scikit-suprise`
- [ ] Download course materials

- [ ] Describe `Recommender Systems`

#### Install `anaconda`, `scikit-suprise`, & _course materials_

## Steps
1. Install Anaconda. See install instructions [mac](https://gist.github.com/ryanorsinger/7d89ad58901b5590ec3e1f23d7b9f887)

2. Download course materials [here](http://media.sundog-soft.com/RecSys/RecSys-Materials.zip) 

3. Download dataset for Movie recommenations [here](http://media.sundog-soft.com/RecSys/ml-latest-small.zip)

4. To open `anaconda-navigator` from CLI open a terminal session and typed

```s
anaconda-navigator
```

5. Click `Environments`. Click `Create`. Name the _environment_ `RecSys`. Select the `Python` runtime. 

6. Using the `anaconda-navigator` you can click _terminal_, when a terminal window opens, run the following command:

```s 
conda install -c conda-forge scikit-surprise
```

7. Select the `RecSys` environment on `anaconda-navigator` and select `Home` tab. 

8. On the `Home` dashboard the IDE we will use is called `Spyder` so click on this tile, and select `Install`. 

-------

### Desribe Recommender Systems

#### Types of Recommender systems 
> Recommender systems find correlations amongst items based on actions a user may take. There is no human curation involved at all. The correlations are historical and typically are based on behavior. When deciding if recommender system or not, ask yourself **"Which system is personalized based on your past expressions of interest?"**

- [ ] _Product_ recommendation systems
- [ ] _Content_ recommenation systems
- [ ] _Music_ recommenation systems
- [ ] _People / Compatibility_ recommenation systems
- [ ] _Search Results_ recommenation systems

#### So how do they work? 
- Implicit vs. Explicit ratings

> Implicit Ratings: Things you click on, things you purchase, things you consume (e.g. # of mins watching a Youtube video, purchasing data, click data)

> Explicit Ratings: Survey responses. (e.g. 4-Stars, NPS scores, etc.)

#### Terminology
> Top-N recommender systems -- presents "n"-number of recommended results. **Think which system retrieves results (top results not all) in a order of precedence according to you past expression of interest?**

#### Typical Top-N topology

- Components of a Top-N System: 
1. Candidate generation
2. Filtering
3. Ranking

_Item Based Collaborative Filtering_ (Amazon Model)
<p align="center">
<img width="350" src="https://user-images.githubusercontent.com/8760590/206545310-2fb7549f-ef79-4a23-9bc6-107e2bdb5d10.png"/>
</p>

another way 

(Not as efficient -- but possibly work for a small catalog of items)
_
<p align="center">
<img width="350" src="https://user-images.githubusercontent.com/8760590/206546085-d997e5c5-f872-448b-9e63-0686cfa80a67.png"/>
</p>

-------

## Reference
- [ ] [Sundog Education](https://www.sundog-education.com/)
- [ ] [Sundog Education - Recommender Systems](https://www.sundog-education.com/RecSys)
- [ ] [Anaconda Distribution](https://www.anaconda.com/products/distribution)
- [ ] [Install Anaconda on Mac](https://gist.github.com/ryanorsinger/7d89ad58901b5590ec3e1f23d7b9f887)