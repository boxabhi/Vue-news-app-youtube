<template>
  <div class="home">
      <div class="p-5">
    <h2 class="text-center">News App using Vue</h2>
    <p class="text-center">Total news  <d-badge theme="primary">{{news.length}}</d-badge></p>
      </div>

    <d-container>
     <d-form @submit="handleOnSubmit()" >
        <d-row>
      <d-col>
        <div class="form-group">
            <label class="sr-only" for="f2_Email">Email Address</label>
            <d-input  class="mb-2 mr-sm-2 mb-sm-0" v-model="search" placeholder="Search news" required />
            </div>
      </d-col>
       <d-col>
         <d-form-select v-model="country" class="mb-3">
      <option :value="null">Select an option</option>
      <option value="in">🍕INDIA</option>
      <option value="us" >🍝 USA</option>
    
    </d-form-select>
       </d-col>
        </d-row>
     </d-form>

     <div class="text-center mb-5">
     <d-button type="submit" @click="handleOnSubmit">Submit</d-button>
     </div>
    </d-container>

    <d-container class="dr-example-container">
      <div class="text-center" v-if="loading">
      <div class="spinner-border text-primary" role="status">
  <span class="sr-only">Loading...</span>
</div>
<p>Getting news for you 😎</p>
      </div>

    <d-row v-if="!loading">

      <d-col cols="12" md="6" lg="3" sm=6 v-for="(news,index) in news" :key="index" class="mt-4">
        <d-card>
                    <d-card-img :src="news.urlToImage" top />
                    <d-card-body>
                        <div class="p-0 m-0 text-dark"><b>{{(news.title)}}</b></div>
                      <p>{{news.description}}</p>
                    </d-card-body>

                    <a :href="news.url" target="_blank"><d-button squared  theme="success" class="btn-block">Read full news</d-button></a>
                </d-card>
      </d-col>
  
    </d-row>
    </d-container>


<footer class="bg-dark p-4 mt-5">
  <p class="text-center text-white">Vue News App</p>
</footer>


  </div>
</template>
<script>
export default {
  data () {
    return {
        search: '',
        url : 'http://newsapi.org/v2/top-headlines',
        news : [
        {
            "source": {
                "id": null,
                "name": "Bitbo.io"
            },
            "author": "cgimmer",
            "title": "Show HN: Bitbo – Real-Time Bitcoin Dashboard",
            "description": "Article URL: https://bitbo.io/\nComments URL: https://news.ycombinator.com/item?id=24968869\nPoints: 2\n# Comments: 0",
            "url": "https://bitbo.io",
            "urlToImage": "https://firebasestorage.googleapis.com/v0/b/bitbo-btc.appspot.com/o/images%2Fog-image.png?alt=media&token=9c0953c4-83b3-4469-9b00-bcff396eb2ad",
            "publishedAt": "2020-11-02T15:09:40Z",
            "content": "Blockchain Stats\r\nTime Since Last Block\r\nMoney Supply\r\nTotal Transactions\r\nDifficulty Stats\r\nEstimated Difficulty Change\r\nBlocks To Retarget\r\nEstimated Retarget Date\r\nLast Difficulty Change\r\nMining S… [+1270 chars]"
        },
        {
            "source": {
                "id": null,
                "name": "Bitcoinist"
            },
            "author": "Tony Spilotro",
            "title": "Bitcoin’s Higher High Shows Just How Weak Fiat Currencies are Becoming",
            "description": "Over the weekend, Bitcoin set a pivotal higher high. And although the crypto asset is pulling back slightly with this week’s election uncertainty, a confirmed uptrend could make for clear skies in the weeks ahead. However, does a lack of a higher high on othe…",
            "url": "https://bitcoinist.com/a-lack-of-bitcoin-higher-high-in-other-currencies-highlights-dollars-decline/",
            "urlToImage": "https://bitcoinist.com/wp-content/uploads/2020/11/bitcoin-btcusd-btceur-btcgbp-btcjpy-Depositphotos_298925140_xl-2015-1920x931.jpg",
            "publishedAt": "2020-11-02T15:00:53Z",
            "content": "Over the weekend, Bitcoin set a pivotal higher high. And although the crypto asset is pulling back slightly with this week’s election uncertainty, a confirmed uptrend could make for clear skies in th… [+2916 chars]"
        },
        {
            "source": {
                "id": null,
                "name": "Cointelegraph"
            },
            "author": "Cointelegraph By Michaël van de Poppe",
            "title": "Ethereum price faces a potential 30% correction after failing to break $400",
            "description": "Ether price is struggling despite Bitcoin rising, which may embolden the bears to push the price down below $300 before another major rally can occur.",
            "url": "https://cointelegraph.com/news/ethereum-price-faces-a-potential-30-correction-after-failing-to-break-400",
            "urlToImage": "https://s3.cointelegraph.com/uploads/2020-11/11adf8b9-ef92-4274-8095-bfa0e33eeed4.jpg",
            "publishedAt": "2020-11-02T15:00:00Z",
            "content": "The cryptocurrency market momentum has swung back to Bitcoin (BTC) recently as BTC dominance and trading volumes have been climbing along with the price. In that regard, the primary altcoin indicator… [+3794 chars]"
        },
        {
            "source": {
                "id": null,
                "name": "Forbes"
            },
            "author": "Robert Farrington, Senior Contributor, \n Robert Farrington, Senior Contributor\n https://www.forbes.com/sites/robertfarrington/",
            "title": "Cryptocurrency Savings Accounts: Will This New Trend Help You Boost Earnings?",
            "description": "Cryptocurrency savings accounts tout high interest rates, but is your money really safe?",
            "url": "https://www.forbes.com/sites/robertfarrington/2020/11/02/cryptocurrency-savings-accounts-will-this-new-trend-help-you-boost-earnings/",
            "urlToImage": "https://thumbor.forbes.com/thumbor/fit-in/1200x0/filters%3Aformat%28jpg%29/https%3A%2F%2Fspecials-images.forbesimg.com%2Fimageserve%2F5f9a54f53fbb0d6eca4c330e%2F0x0.jpg",
            "publishedAt": "2020-11-02T14:50:00Z",
            "content": "Investing in cryptocurrency may seem like a huge gamble, but the bet has paid off tremendously for those who invested in the right type of crypto at the right time. \r\nIn November of 2015, you could b… [+5941 chars]"
        },
        {
            "source": {
                "id": "business-insider",
                "name": "Business Insider"
            },
            "author": "bwinck@businessinsider.com (Ben Winck)",
            "title": "Dow rallies 310 points after posting biggest weekly slide since March",
            "description": "\"The stock market will undoubtedly take a wait and see attitude\" until election results materialize, Marc Chaikin, founder of Chaikin Analytics, said.",
            "url": "https://www.businessinsider.com/stock-market-news-today-indexes-presidential-election-fomc-meeting-oil-2020-11",
            "urlToImage": "https://images2.markets.businessinsider.com/5fa00af86f5b310011724bb6?format=jpeg",
            "publishedAt": "2020-11-02T14:42:00Z",
            "content": "Drew Angerer/Getty Images\r\n<ul><li>US stocks gained on Monday, as investors looked to rebound from the market's worst week since March.</li><li>Equities are set to face heightened volatility as elect… [+4505 chars]"
        },
        {
            "source": {
                "id": null,
                "name": "Seeking Alpha"
            },
            "author": "Bram de Haas",
            "title": "The Rise Of Overstock.com",
            "description": "Overstock.com has had an incredibly run in 2020 but recently corrected significantly. After following Overstock.com for years I'm revisiting the company to see if it is a buy today.",
            "url": "https://seekingalpha.com/article/4383994-rise-of-overstock-com",
            "urlToImage": "https://static1.seekingalpha.com/uploads/2020/11/1/saupload_14de776d4cec887e626221a2403550f7.png",
            "publishedAt": "2020-11-02T14:37:42Z",
            "content": "My first article on Seeking Alpha bullish on Bitcoin dates back to July 5, 2016. I've followed it up with quite a few follow-ups. I took a break from writing about this interesting new asset class af… [+8815 chars]"
        },
        {
            "source": {
                "id": "business-insider",
                "name": "Business Insider"
            },
            "author": "Martin Coulter",
            "title": "New data shows the 10 best UK universities for founders raising their first $1 million after graduating",
            "description": "Summary List Placement\n\nNew data has revealed which universities produce the startup founders who are fastest to raise their first £1 million (or $1.3 million) after graduation. \nWhile institutions such as the University of Oxford, the University of Cambridge…",
            "url": "https://www.businessinsider.com/top-10-universities-for-startup-founders-to-raise-1-million-2020-11",
            "urlToImage": "https://i.insider.com/5fa017ae69331a0011bc6a6f?width=1200&format=jpeg",
            "publishedAt": "2020-11-02T14:32:28Z",
            "content": "New data has revealed which universities produce the startup founders who are fastest to raise their first £1 million (or $1.3 million) after graduation. \r\nWhile institutions such as the University o… [+932 chars]"
        },
        {
            "source": {
                "id": null,
                "name": "Telegraaf.nl"
            },
            "author": "redactie DFT",
            "title": "Bitcoin blaast stoom af in aanloop naar verkiezingen VS",
            "description": "De digitale munt bitcoin moest maandag flink terrein prijsgeven nadat in de voorbije maand nog de beste rit omhoog sinds april werd gemaakt.",
            "url": "https://www.telegraaf.nl/financieel/969802594/bitcoin-blaast-stoom-af-in-aanloop-naar-verkiezingen-vs",
            "urlToImage": "https://www.telegraaf.nl/images/1200x630/filters:format(jpeg):quality(80)/cdn-kiosk-api.telegraaf.nl/acc68cca-1d17-11eb-8f38-0255c322e81b.jpg",
            "publishedAt": "2020-11-02T14:26:52Z",
            "content": "De bitcoin viel rond 15.00 uur (Nederlandse tijd) 3% terug op $13.400 nadat dit weekend de grens van 14.000 werd gepasseerd naar het hoogste niveau in ruim twee jaar.\r\nOver de gehele maand oktober de… [+744 chars]"
        },
        {
            "source": {
                "id": null,
                "name": "CoinDesk"
            },
            "author": "Benjamin Powers",
            "title": "Decentralized VPN Sees Increased Use in Nigeria Amid #EndSars Protests",
            "description": "Nigerians are protesting police corruption and concerns about a possible internet shutdown have driven some to adopt decentralized VPNs like Mysterium.",
            "url": "https://www.coindesk.com/index.php?p=539914",
            "urlToImage": "https://static.coindesk.com/wp-content/uploads/2020/10/tobi-oshinnaike-NrXJUWDFVWU-unsplash-1200x628.jpg",
            "publishedAt": "2020-11-02T14:24:15Z",
            "content": "The Takeaway:\r\n<ul><li>Nigerians are adopting more VPNs, including decentralized VPNs.</li><li>The adoption comes as #EndSARS protestors are concerned the government may limit access to parts of the … [+9364 chars]"
        },
        {
            "source": {
                "id": null,
                "name": "CoinDesk"
            },
            "author": "Zack Voell",
            "title": "Bitcoin Miners Saw 8% Revenue Increase in October",
            "description": "12% of revenue came from fees, the highest percentage since Jan. 2018.",
            "url": "https://www.coindesk.com/bitcoin-miner-revenue-october-2020",
            "urlToImage": "https://static.coindesk.com/wp-content/uploads/2020/11/october-miner2-1200x628.png",
            "publishedAt": "2020-11-02T14:16:02Z",
            "content": "Bitcoin miners generated an estimated $353 million in revenue in October, up 8% from September, according to on-chain data from Coin Metrics analyzed by CoinDesk.\r\nThe revenue increase came as bitcoi… [+1713 chars]"
        },
        {
            "source": {
                "id": null,
                "name": "CoinDesk"
            },
            "author": "Bradley Keoun",
            "title": "First Mover: Bitcoin Retreats Before U.S. Election After Dominating Crypto in October",
            "description": "Bitcoin had an unusually bullish October, with a 29% gain that led the monthly performance ranking of digital assets in the CoinDesk 20.",
            "url": "https://www.coindesk.com/index.php?p=540235",
            "urlToImage": "https://static.coindesk.com/wp-content/uploads/2020/11/MOSHED-2020-11-2-7-59-56-1200x628.jpg",
            "publishedAt": "2020-11-02T14:03:03Z",
            "content": "Bitcoin was lower around $13,200, retreating after reaching a fresh 2020 high near $14,100 on Oct. 31. \r\nTuesday’s presidential election in the U.S. “is going to be the driving force for global marke… [+6078 chars]"
        },
        {
            "source": {
                "id": null,
                "name": "Cointelegraph"
            },
            "author": "Cointelegraph By Andrey Shevchenko",
            "title": "A new DeFi project could let smart contracts buy physical goods",
            "description": "Boson Protocol is set to develop a trustless escrow mechanism with its $350,000 funding round.",
            "url": "https://cointelegraph.com/news/a-new-defi-project-could-let-smart-contracts-buy-physical-goods",
            "urlToImage": "https://s3.cointelegraph.com/uploads/2020-11/1f22c079-aa74-4031-91b3-5dbeef179c32.jpg",
            "publishedAt": "2020-11-02T13:56:21Z",
            "content": "Boson Protocol, a project that seeks to connect the real world of physical commerce to smart contracts, has announced a successful $350,000 seed round on Monday.\r\nThe project is creating the building… [+2421 chars]"
        },
        {
            "source": {
                "id": null,
                "name": "Yahoo Entertainment"
            },
            "author": "Yahoo Finance Video",
            "title": "Yahoo Finance Presents: Bridgewater Associates Founder Ray Dalio",
            "description": "In this episode of Yahoo Finance Presents, correspondent Julia La Roche speaks with Bridgewater Associates Founder Ray Dalio about the current state of the world as well as the 2020 election and U.S. wealth gap.",
            "url": "https://finance.yahoo.com/video/yahoo-finance-presents-ray-dalio-134300010.html",
            "urlToImage": "https://s.yimg.com/hd/cp-video-transcode/prod/2020-10/30/5f9b35363b6d0e09c78f5f1d/5f9c38b8e6126015317ec33c_o_U_v3.jpg",
            "publishedAt": "2020-11-02T13:43:00Z",
            "content": "In this episode of Yahoo Finance Presents, correspondent Julia La Roche speaks with Bridgewater Associates Founder Ray Dalio about the current state of the world as well as the 2020 election and U.S.… [+14333 chars]"
        },
        {
            "source": {
                "id": null,
                "name": "Practical Ecommerce"
            },
            "author": "Sig Ueland",
            "title": "Ecommerce Product Releases: November 2, 2020",
            "description": "Here is a list of product releases and updates for late October from companies that offer services to online merchants. There are updates on social commerce, discounted shipping, holiday deals, live chat, analytics, and content creation.\nThe post Ecommerce Pr…",
            "url": "https://www.practicalecommerce.com/ecommerce-product-releases-november-2-2020",
            "urlToImage": "https://www.practicalecommerce.com/wp-content/uploads/2020/10/thumb-4.jpg",
            "publishedAt": "2020-11-02T13:42:43Z",
            "content": "Here is a list of product releases and updates for late October from companies that offer services to online merchants. There are updates on social commerce, discounted shipping, holiday deals, live … [+6871 chars]"
        },
        {
            "source": {
                "id": null,
                "name": "PRNewswire"
            },
            "author": null,
            "title": "Chad C. Meek, Author, Futurist Has Just Released a Book Entitled The New Libertarian Party, Revolution for America",
            "description": "SAN DIEGO, Nov. 2, 2020 /PRNewswire/ -- In his thought-provoking book, Meek points out how the 1% has co-opted the United States political system and government, which has marginalized the American People into a separate downtrodden serfdom class of citizens.…",
            "url": "https://www.prnewswire.com/news-releases/chad-c-meek-author-futurist-has-just-released-a-book-entitled-the-new-libertarian-party-revolution-for-america-301164283.html",
            "urlToImage": "https://mma.prnewswire.com/media/1324479/Giant_Rock.jpg?p=facebook",
            "publishedAt": "2020-11-02T13:42:00Z",
            "content": "SAN DIEGO, Nov. 2, 2020 /PRNewswire/ -- In his thought-provoking book, Meek points out how the 1% has co-opted the United States political system and government, which has marginalized the American P… [+2298 chars]"
        },
        {
            "source": {
                "id": null,
                "name": "CNBC"
            },
            "author": "Jesse Pound",
            "title": "The best 'blue wave' trade could be this muni bond ETF and bitcoin, strategist says",
            "description": "MKM Partners' Michael Darda explained why some non-stock assets could be good investment plays if the Democrats sweep the election.",
            "url": "https://www.cnbc.com/2020/11/02/the-best-blue-wave-trade-could-be-this-muni-bond-etf-and-bitcoin-strategist-says.html",
            "urlToImage": "https://image.cnbcfm.com/api/v1/image/106668476-15977683532020-08-18t094644z_966918122_rc29gi95b8sg_rtrmadp_0_usa-spac-wallstreet.jpeg?v=1597768393",
            "publishedAt": "2020-11-02T13:41:26Z",
            "content": "(This story is for CNBC Pro subscribers only).\r\nInvestors should consider preparing for the possibility of a Democratic sweep on Tuesday by taking stakes in two asset classes outside of stocks, said … [+488 chars]"
        },
        {
            "source": {
                "id": null,
                "name": "Activistpost.com"
            },
            "author": "Activist Post",
            "title": "Archbishop Warns Trump About “The Great Reset”",
            "description": "By Neenah Payne Carlo Maria Vigano, Tit. Archbishop of Ulpiana, Former Apostolic Nuncio to the United States of America wrote President Trump on June 7....\nArchbishop Warns Trump About “The Great Reset”",
            "url": "https://www.activistpost.com/2020/11/archbishop-warns-trump-about-the-great-reset.html",
            "urlToImage": "https://www.activistpost.com/wp-content/uploads/2020/11/Embedded1604280162498.png",
            "publishedAt": "2020-11-02T13:36:07Z",
            "content": "By Neenah Payne\r\nCarlo Maria Vigano, Tit. Archbishop of Ulpiana, Former Apostolic Nuncio to the United States of America wrote President Trump on June 7. Trump praises Italian archbishop who urges hi… [+22977 chars]"
        },
        {
            "source": {
                "id": null,
                "name": "newsBTC"
            },
            "author": "Tony Spilotro",
            "title": "Bitcoin Price Sinks $6% From Weekend Highs As Election Day Approaches",
            "description": "Bitcoin price set a new higher high this weekend at over $14,000 and closed the highest monthly candle since December 2017, leaving just one higher monthly close to beat. However, before that could happen, the leading cryptocurrency by market cap has been dra…",
            "url": "https://www.newsbtc.com/analysis/btc/bitcoin-price-sinks-6-from-weekend-highs-as-election-day-approaches/",
            "urlToImage": "https://www.newsbtc.com/wp-content/uploads/2020/11/bitcoin-election-2020-Depositphotos_188865352_xl-2015-scaled.jpg",
            "publishedAt": "2020-11-02T13:26:39Z",
            "content": "Bitcoin price set a new higher high this weekend at over $14,000 and closed the highest monthly candle since December 2017, leaving just one higher monthly close to beat.\r\nHowever, before that could … [+1743 chars]"
        },
        {
            "source": {
                "id": null,
                "name": "The Indian Express"
            },
            "author": "Express Web Desk",
            "title": "Bengaluru: 10 held for buying drugs on dark web, narcotics worth Rs 90 lakh seized",
            "description": "Police said the accused were paying for the drugs using bitcoins, and getting parcels delivered as gift packs from abroad, including through India Post.",
            "url": "https://indianexpress.com/article/cities/bangalore/bengaluru-10-held-for-procuring-drugs-through-dark-web-6914000/",
            "urlToImage": "https://images.indianexpress.com/2020/11/drugs-1200.jpg",
            "publishedAt": "2020-11-02T13:22:25Z",
            "content": "The drugs seized by Bengaluru Central Crime Branch police. In a special drive by Bengaluru Central Crime Branch(CCB) police against drugs purchased through the dark net using bitcoins, eight cases ha… [+2122 chars]"
        },
        {
            "source": {
                "id": null,
                "name": "Pypi.org"
            },
            "author": "alphaazeta@protonmail.com",
            "title": "alphazeta.warden added to PyPI",
            "description": "Private Portfolio Tool - Specter Server Edition",
            "url": "https://pypi.org/project/alphazeta.warden/",
            "urlToImage": "https://pypi.org/static/images/twitter.90915068.jpg",
            "publishedAt": "2020-11-02T13:20:18Z",
            "content": "This is a light weight version of the original WARden designed for integration with Specter Server.\r\nTransactions will be imported automatically from Specter.\r\nThis app was built with a couple of goa… [+3741 chars]"
        }
    ],
        API_KEY : '827705eea42e455cba8bf4afafc7da90',
        country : 'us',
        loading : false
        
      
    }
  },

  methods: {
    handleOnSubmit (e) {
      this.loading = true
      e.preventDefault();
      
      var search = this.search
      var country = this.country
      var url = `${this.url}?apiKey=${this.API_KEY}`

      if(search){
      //  url = `${url}&q=${search}`
      }
      
      if(country){
        url = `${url}&country=${country}`
      }
      var cros = 'https://cors-anywhere.herokuapp.com/'
  console.log(cros + url)
      fetch(cros + url)
      .then(res => res.json())
      .then(result =>{
        console.log(result)
        this.news = result.articles
        this.loading = false
      })

      
    }
  },
  mounted (){
    
  }
}
</script>
