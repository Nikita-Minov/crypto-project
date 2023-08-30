<script setup lang="ts">

  useSeoMeta({
    title: 'BitList',
    ogTitle: 'BitList',
    description: 'BitList is a crypto exchange.',
    ogDescription: 'BitList is a crypto exchange',
  })

  const coins = [
    {name: '1inch', code: '1INCH', icon: '/coins/1inch.svg', value: '-', change: 0, negative: false},
    {name: 'Bitcoin', code: 'BTC', icon: '/coins/bitcoin.svg', value: '-', change: 0, negative: false},
    {name: 'Ethereum', code: 'ETH', icon: '/coins/ethereum.svg', value: '-', change: 0, negative: false},
    {name: 'Binance Coin', code: 'BNB', icon: '/coins/binance-coin.svg', value: '-', change: 0, negative: false},
    {name: 'Binance USD', code: 'BUSD', icon: '/coins/binance-usd.svg', value: '-', change: 0, negative: false},
    {name: 'Polygon', code: 'MATIC', icon: '/coins/polygon.svg', value: '-', change: 0, negative: false},
  ];


  for (const coin of coins) {
    const { data } = await useFetch(`https://min-api.cryptocompare.com/data/price?tryConversion=false&fsym=${coin.code}&tsyms=USD`, {
      headers: {
        'Authorization': 'Apikey ' + process.env.TOKEN,
      }
    });
    if(!data?.value['USD']) continue;
    coin.value = data.value[`USD`];
  }

  for(const coin of coins) {
    const { data } = await useFetch(`https://min-api.cryptocompare.com/data/v2/histoday?tryConversion=false&fsym=${coin.code}&tsym=USD&limit=1`, {
      headers: {
        'Authorization': 'Apikey ' + process.env.TOKEN,
      }
    });
    if(!data.value.Data.Data[0].open) continue;
    const change = data.value.Data.Data[0].open/coin.value;
    if(change >= 1) {
      coin.negative = true;
      coin.change = (+((change - 1)))*100;
      coin.change = +coin.change.toFixed(2);
    } else {
      coin.negative = false;
      coin.change = (+((1- change)))*100;
      coin.change = +coin.change.toFixed(2);
    }
  }
</script>

<template>
  <div class="wrapper wrapper-bg-border">
    <section class="main">
      <div class="left-block">
        <h1 class="left-block__header">
          Decentralized crypto platform
        </h1>
        <h2 class="left-block__subtitle">
          Buy, trade and store cryptocurrencies
        </h2>
        <div class="input-block">
          <div class="input-wrapper">
            <input type="text" class="input-wrapper__input" placeholder="Example@gmail.com">
          </div>
          <button class="input-block__signin-btn">Sign in</button>
        </div>
      </div>
      <div class="right-block">
        <img src="../assets/img/graph.png" class="right-block__graph" alt="graph">
      </div>
    </section>
    <section class="courses">
      <div class="courses-table">
        <div class="courses-table__row">
          <div class="courses-table__row__item courses-table__head__item-start">
            <p class="courses-table__head__item__text">
              Asset
            </p>
          </div>
          <div class="courses-table__row__item courses-table__head__item-center">
            <p class="courses-table__head__item__text">
              Price
            </p>
          </div>
          <div class="courses-table__row__item courses-table__head__item-center">
            <p class="courses-table__head__item__text">
              Change
            </p>
          </div>
          <div class="courses-table__row__item courses-table__head__item-center">
            <p class="courses-table__head__item__text">
              Volume
            </p>
          </div>
        </div>

        <div class="courses-table__row" v-for="coin of coins">
          <div class="courses-table__row__item courses-table__head__item-start">
            <div class="coin">
              <img :src='coin.icon' class="coin__img" alt="coin">
              <p class="coin__name">{{coin.name}}</p>
              <p class="coin__code">{{coin.code}}</p>
            </div>
          </div>
          <div class="courses-table__row__item courses-table__head__item-center">
            <p class="price">
              $ {{coin.value}}
            </p>
          </div>
          <div class="courses-table__row__item courses-table__head__item-center">
            <p :class="[coin.negative ? 'change change-negative' : 'change change-positive']">
              {{coin.change}} %
            </p>
          </div>
          <div class="courses-table__row__item courses-table__head__item-center">
            <p class="volume">
              2.000.000M
            </p>
          </div>
          <div class="courses-table__row__item courses-table__head__item-center">
            <button class="trade-button">
              Trade
            </button>
          </div>
        </div>
      </div>
      <button class="view-more-btn">All assets</button>
    </section>
  </div>
  <div class="wrapper">
    <section class="exchanges">
      <div class="exchanges__block">
        <h1 class="exchanges__block__title">
          Bitles is your reliable guide in the world of digital assets
        </h1>
        <p class="exchanges__block__desc">
          The Bitles app is a comprehensive solution for trading digital assets. Buy and sell cryptocurrencies quickly and openly, comfortably and safely from anywhere in the world.
        </p>
      </div>
      <div class="exchanges__block exchanges__block-flex">
        <img src="/img/exchanges.png" class="exchanges-img" alt="exchanges">
      </div>
    </section>
  </div>
  <div class="line"></div>
  <div class="wrapper">
    <section class="advantages">
      <div class="advantages-block">
        <div class="advantage-card">
          <img src="/advantages/1.svg" class="advantage-card__img" alt="1">
          <h4 class="advantage-card__title">
            User Safe Asset Fund (SAFU)world.
          </h4>
          <p class="advantage-card__desc">
            Bitlist holds 10% of all trading fees in a protected asset fund to protect a portion of user funds.
          </p>
        </div>
        <div class="advantage-card">
          <img src="/advantages/2.svg" class="advantage-card__img" alt="1">
          <h4 class="advantage-card__title">
            User Access Control
          </h4>
          <p class="advantage-card__desc">
            Personalized access control allows you to limit the devices and addresses that can access your account.
          </p>
        </div>
        <div class="advantage-card">
          <img src="/advantages/3.svg" class="advantage-card__img" alt="1">
          <h4 class="advantage-card__title">
            Improved data encryption
          </h4>
          <p class="advantage-card__desc">
            Your transaction data is encrypted - only you can access your personal data.
          </p>
        </div>
        <div class="advantage-card">
          <img src="/advantages/4.svg" class="advantage-card__img" alt="1">
          <h4 class="advantage-card__title">
            Support 24/7
          </h4>
          <p class="advantage-card__desc">
            24/7 real-time support is always ready to help you.
          </p>
        </div>
        <div class="advantage-card">
          <img src="/advantages/5.svg" class="advantage-card__img" alt="1">
          <h4 class="advantage-card__title">
            Fast replineshments and withdraws
          </h4>
          <p class="advantage-card__desc">
            Transfer funds to and from your accounts quickly and easily.
          </p>
        </div>
        <div class="advantage-card">
          <img src="/advantages/6.svg" class="advantage-card__img" alt="1">
          <h4 class="advantage-card__title">
            Comfortable P2P platform
          </h4>
          <p class="advantage-card__desc">
            Top up your account in any convenient way on the P2P platform at favorable rates.
          </p>
        </div>
      </div>
    </section>
  </div>
  <div class="line"></div>
  <div class="wrapper wrapper-bg-register">
    <section class="register-section">
      <h1 class="register-section__title">
        Register your account now and start to trade
      </h1>
      <div class="register-block">
        <div class="input-wrapper">
          <input type="text" class="input-wrapper__input" placeholder="Example@gmail.com">
        </div>
        <button class="input-block__signin-btn">Sign in</button>
      </div>
    </section>
  </div>
</template>

<style>
@import url('~/styles/pages/index.css');
</style>