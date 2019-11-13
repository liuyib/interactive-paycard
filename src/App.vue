<template>
  <div id="app" class="app">
    <div class="app-form">
      <div class="app-card__wrapper">
        <div class="app-card">
          <div class="app-card__inner">
            <div class="app-card-header">
              <img
                class="app-card-header__chip"
                :src="require('@/assets/chip.png')"
                alt="Card Chip"
              />
              <img
                class="app-card-header__type"
                :src="require('@/assets/visa.png')"
                alt="Card Type"
              />
            </div>

            <div class="app-card-content">
              <label class="app-card-content-number" for="card-number">
                <span v-for="i in [0, 1, 2, 3, 4, 5, 6, 7]" :key="i">
                  <div class="app-card-content-number__item">#</div>
                </span>
              </label>
            </div>

            <div class="app-card-footer">
              <label class="app-card-footer-name" for="card-name">
                <div class="app-card-footer-name__holder">Card Holder</div>
                <div class="app-card-footer-name__text">FULL NAME</div>
              </label>
              <div class="app-card-footer-date">
                <div class="app-card-footer-date__expires">Expires</div>
                <label class="app-card-footer-date__text" for="card-month">MM</label>
                <span>/</span>
                <label class="app-card-footer-date__text" for="card-year">YY</label>
              </div>
            </div>
          </div>

          <div class="app-card-cover">
            <img class="app-card-cover__bg" :src="require('@/assets/11.jpeg')" alt="Card Cover" />
          </div>
        </div>
      </div>

      <div class="app-form__inner">
        <div class="app-form-input">
          <label class="app-form-input__label" for="card-number">Card Number</label>
          <input class="app-form-input__input" id="card-number" type="text" />
        </div>
        <div class="app-form-input">
          <label class="app-form-input__label" for="card-name">Card Holders</label>
          <input class="app-form-input__input" id="card-name" type="text" />
        </div>
        <div class="app-form__row">
          <div class="app-form__col app-form__group">
            <label class="app-form-input__label" for="card-month">Expiration Date</label>
            <select class="app-form-input__input --select" id="card-month">
              <option value disabled="disabled" selected="selected">Month</option>
            </select>
            <select class="app-form-input__input --select" id="card-year">
              <option value disabled="disabled" selected="selected">Year</option>
            </select>
          </div>

          <div class="app-form__col">
            <div class="app-form-input">
              <label class="app-form-input__label" for="card-cvv">CVV</label>
              <input class="app-form-input__input" id="card-cvv" type="text" />
            </div>
          </div>
        </div>

        <button class="app-form__submit">Submit</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "app",
  data() {
    return {};
  },
  methods: {}
};
</script>
<style lang="stylus">
@import url('https://fonts.googleapis.com/css?family=Source+Code+Pro:400,500,600,700|Source+Sans+Pro:400,600,700&display=swap');

*, *::before, *::after {
  box-sizing: inherit;
}

*:focus {
  outline: none;
}

html {
  box-sizing: border-box;
}

body {
  margin: 0;
  padding: 0;
  background-color: #ddeefc;
  font-family: 'Source Sans Pro', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

.app {
  min-height: 100vh;

  &-form {
    margin: auto;
    width: 100%;
    height: 100%;
    max-width: 570px;

    &__inner {
      border-radius: 10px;
      padding: 180px 35px 35px 35px;
      background-color: #fff;
      box-shadow: 0 30px 60px 0 rgba(90, 116, 148, 0.4);
    }

    &-input {
      margin-bottom: 20px;

      &__label {
        display: block;
        margin-bottom: 5px;
        width: 100%;
        font-size: 14px;
        font-weight: 500;
        color: #1a3b5d;
        user-select: none;
      }

      &__input {
        border: 1px solid #ced6e0;
        border-radius: 5px;
        padding: 5px 15px;
        width: 100%;
        height: 50px;
        box-shadow: none;
        font-family: 'Source Sans Pro', sans-serif;
        font-size: 18px;
        background: none;
        color: #1a3b5d;
        transition: all 0.3s ease-in-out;
      }

      &__group {
        display: flex;
        flex: 1;
        align-items: flex-start;
        flex-wrap: wrap;
      }

      &.--select {
        -webkit-appearance: none;
        background-size: 12px;
        background-position: 90% center;
        background-repeat: no-repeat;
        padding-right: 30px;
      }
    }

    &__row {
      display: flex;
      align-items: flex-start;
    }

    &__col {
      flex: auto;

      &:not(:last-child) {
        margin-right: 35px;
      }
    }

    &__submit {
      width: 100%;
      height: 55px;
      background: #2364d2;
      border: none;
      border-radius: 5px;
      font-size: 22px;
      font-weight: 500;
      font-family: 'Source Sans Pro', sans-serif;
      box-shadow: 3px 10px 20px 0px rgba(35, 100, 210, 0.3);
      color: #fff;
      margin-top: 20px;
      cursor: pointer;
    }
  }

  &-card {
    overflow: hidden;
    border-radius: 15px;
    height: 100%;
    box-shadow: 0 20px 60px 0 rgba(14, 42, 90, 0.55);
    transform: perspective(2000px) rotateY(0deg) rotateX(0deg) rotate(0deg);
    transform-style: preserve-3d;
    transition: all 0.8s cubic-bezier(0.71, 0.03, 0.56, 0.85);
    backface-visibility: hidden;

    &__wrapper {
      z-index: 2;
      position: relative;
      margin: 0 auto -130px auto;
      width: 100%;
      height: 270px;
      max-width: 430px;
    }

    &__inner {
      font-family: 'Source Code Pro', monospace;
      padding: 25px 15px;
      position: relative;
      z-index: 4;
      height: 100%;
      text-shadow: 7px 6px 10px rgba(14, 42, 90, 0.8);
      user-select: none;
    }

    &-cover {
      z-index: -1;
      position: absolute;
      top: 0;
      left: 0;
      overflow: hidden;
      border-radius: 15px;
      width: 100%;
      height: 100%;
      background-color: #1c1d27;

      &::after {
        content: '';
        position: absolute;
        left: 0;
        top: 0;
        width: 100%;
        height: 100%;
        background: rgba(6, 2, 29, 0.45);
      }

      &__bg {
        display: block;
        max-width: 100%;
        max-height: 100%;
        width: 100%;
        height: 100%;
      }
    }

    &-header {
      display: flex;
      align-items: flex-start;
      justify-content: space-between;
      margin-bottom: 40px;
      padding: 0 10px;

      &__chip {
        width: 60px;
      }

      &__type {
        height: 45px;
      }
    }

    &-content {
      margin-bottom: 35px;
      padding: 10px 15px;

      &-number {
        font-weight: 500;
        line-height: 1;
        color: #fff;
        font-size: 27px;
        cursor: pointer;

        &__item {
          display: inline-block;
          width: 16px;
        }
      }
    }

    &-footer {
      display: flex;
      align-items: flex-start;
      color: #fff;

      &-name {
        display: block;
        padding: 10px 15px;
        width: 100%;
        max-width: calc(100% - 85px);
        font-weight: 500;
        color: #fff;
        cursor: pointer;

        &__holder {
          margin-bottom: 6px;
          opacity: 0.7;
          font-size: 13px;
        }

        &__text {
          max-width: 100%;
          line-height: 1;
          font-size: 18px;
          overflow: hidden;
          white-space: nowrap;
          text-overflow: ellipsis;
          text-transform: uppercase;
        }
      }

      &-date {
        display: inline-flex;
        margin-left: auto;
        padding: 10px;
        width: 80px;
        flex-wrap: wrap;
        white-space: nowrap;
        flex-shrink: 0;
        font-size: 18px;
        cursor: pointer;

        &__expires {
          padding-bottom: 6px;
          width: 100%;
          font-size: 13px;
          opacity: 0.7;
        }

        &__text {
          position: relative;
        }
      }
    }
  }
}
</style>
