<template>
    <!-- error page -->
    <div class="error">
        <div class="container-floud">
            <div class="col-xs-12 ground-color text-center">
                <div class="container-error-404">
                    <div class="clip"><div class="shadow"><span class="digit thirddigit"></span></div></div>
                    <div class="clip"><div class="shadow"><span class="digit seconddigit"></span></div></div>
                    <div class="clip">
                        <a href="https://codepen.io/ahmed_b_hameed/pen/lkqnmp?editors=0010" 
                            target="_blank"
                            style="position: absolute; right: 10px; color: #999999bd;">© reuse</a>
                        <div class="shadow"><span class="digit firstdigit"></span></div></div>
                </div>
                <h2 class="h1 my-4"><em>{{message}}</em></h2>
            </div>
        </div>
    </div>
    <!-- error page -->
</template>

<script>
export default {
  name: "nuxt-error",
  props: ["error"],
  layout() {
    return "df";
  },
  head() {
    return {
      title: this.message,
      meta: [
        {
          name: "viewport",
          content:
            "width=device-width,initial-scale=1.0,minimum-scale=1.0,maximum-scale=1.0,user-scalable=no"
        }
      ],
      link: [
        {
          type: "text/css",
          rel: "stylesheet",
          href:
            "https://fonts.googleapis.com/css?family=Anton|Passion+One|PT+Sans+Caption"
        }
      ]
    };
  },
  mounted() {
    var loop1,
      loop2,
      loop3,
      time = 30,
      i = 0,
      number;

    let numberd = this.statusCode.toString().split("");

    Array.prototype.slice
      .call(document.querySelectorAll(".digit"))
      .reduce((acum, item, index) => {
        let ci = setInterval(
          ({ selector, num }) => {
            if (i > 40) {
              clearInterval(ci);
              selector.textContent = num;
            } else {
              selector.textContent = this.randomNum();
              i++;
            }
          },
          time,
          {
            num: numberd[index],
            selector: item
          }
        );
      }, []);
  },
  methods: {
    randomNum() {
      "use strict";
      return Math.floor(Math.random() * 9) + 1;
    }
  },
  computed: {
    statusCode() {
      return (this.error && this.error.statusCode) || 500;
    },
    message() {
      return this.error.message || "Some error";
    }
  }
};
</script>

<style scoped>
* {
  font-family: "PT Sans Caption", sans-serif, "arial", "Times New Roman";
}
/* Error Page */
.error .container-floud {
  padding-top: 140px;
}
.error .clip .shadow {
  height: 180px; /*Contrall*/
}
.error .clip:nth-of-type(2) .shadow {
  width: 130px; /*Contrall play with javascript*/
}
.error .clip:nth-of-type(1) .shadow,
.error .clip:nth-of-type(3) .shadow {
  width: 250px; /*Contrall*/
}
.error .digit {
  width: 150px; /*Contrall*/
  height: 150px; /*Contrall*/
  line-height: 150px; /*Contrall*/
  font-size: 120px;
  font-weight: bold;
}
.error h2   /*Contrall*/
 {
  font-size: 26px;
}
.error .msg /*Contrall*/
 {
  top: -190px;
  left: 30%;
  width: 80px;
  height: 80px;
  line-height: 80px;
  font-size: 32px;
}
.error span.triangle    /*Contrall*/
 {
  top: 70%;
  right: 0%;
  border-left: 20px solid #535353;
  border-top: 15px solid transparent;
  border-bottom: 15px solid transparent;
}

.error .container-error-404 {
  /* margin-top: 10%; */
  position: relative;
  height: 250px;
  padding-top: 40px;
}
.error .container-error-404 .clip {
  display: inline-block;
  transform: skew(-45deg);
}
.error .clip .shadow {
  overflow: hidden;
}
.error .clip:nth-of-type(2) .shadow {
  overflow: hidden;
  position: relative;
  box-shadow: inset 20px 0px 20px -15px rgba(150, 150, 150, 0.8),
    20px 0px 20px -15px rgba(150, 150, 150, 0.8);
}

.error .clip:nth-of-type(3) .shadow:after,
.error .clip:nth-of-type(1) .shadow:after {
  content: "";
  position: absolute;
  right: -8px;
  bottom: 0px;
  z-index: 9999;
  height: 100%;
  width: 10px;
  background: linear-gradient(
    90deg,
    transparent,
    rgba(173, 173, 173, 0.8),
    transparent
  );
  border-radius: 50%;
}
.error .clip:nth-of-type(3) .shadow:after {
  left: -8px;
}
.error .digit {
  position: relative;
  top: 8%;
  color: white;
  background: #6c757d;
  border-radius: 50%;
  display: inline-block;
  transform: skew(45deg);
}
.error .clip:nth-of-type(2) .digit {
  left: -5%;
}
.error .clip:nth-of-type(1) .digit {
  right: -20%;
}
.error .clip:nth-of-type(3) .digit {
  left: -20%;
}
.error h2 {
  color: #a2a2a2;
  font-weight: bold;
  padding-bottom: 20px;
}
.error .msg {
  position: relative;
  z-index: 9999;
  display: block;
  background: #535353;
  color: #a2a2a2;
  border-radius: 50%;
  font-style: italic;
}
.error .triangle {
  position: absolute;
  z-index: 999;
  transform: rotate(45deg);
  content: "";
  width: 0;
  height: 0;
}

/* Error Page */
@media (max-width: 767px) {
  /* Error Page */
  .error .clip .shadow {
    height: 100px; /*Contrall*/
  }
  .error .clip:nth-of-type(2) .shadow {
    width: 80px; /*Contrall play with javascript*/
  }
  .error .clip:nth-of-type(1) .shadow,
  .error .clip:nth-of-type(3) .shadow {
    width: 100px; /*Contrall*/
  }
  .error .digit {
    width: 80px; /*Contrall*/
    height: 80px; /*Contrall*/
    line-height: 80px; /*Contrall*/
    font-size: 52px;
  }
  .error h2   /*Contrall*/
 {
    font-size: 20px;
  }
  .error .msg /*Contrall*/
 {
    top: -110px;
    left: 15%;
    width: 40px;
    height: 40px;
    line-height: 40px;
    font-size: 18px;
  }
  .error span.triangle    /*Contrall*/
 {
    top: 70%;
    right: -3%;
    border-left: 10px solid #535353;
    border-top: 8px solid transparent;
    border-bottom: 8px solid transparent;
  }
  .error .container-error-404 {
    height: 150px;
  }
  /* Error Page */
}

/*--------------------------------------------Framework --------------------------------*/

.overlay {
  position: relative;
  z-index: 20;
} /*done*/
.ground-color {
  background: white;
} /*done*/
.item-bg-color {
  background: #eaeaea;
} /*done*/

/* Padding Section*/
.padding-top {
  padding-top: 10px;
} /*done*/
.padding-bottom {
  padding-bottom: 10px;
} /*done*/
.padding-vertical {
  padding-top: 10px;
  padding-bottom: 10px;
}
.padding-horizontal {
  padding-left: 10px;
  padding-right: 10px;
}
.padding-all {
  padding: 10px;
} /*done*/

.no-padding-left {
  padding-left: 0px;
} /*done*/
.no-padding-right {
  padding-right: 0px;
} /*done*/
.no-vertical-padding {
  padding-top: 0px;
  padding-bottom: 0px;
}
.no-horizontal-padding {
  padding-left: 0px;
  padding-right: 0px;
}
.no-padding {
  padding: 0px;
} /*done*/
/* Padding Section*/

/* Margin section */
.margin-top {
  margin-top: 10px;
} /*done*/
.margin-bottom {
  margin-bottom: 10px;
} /*done*/
.margin-right {
  margin-right: 10px;
} /*done*/
.margin-left {
  margin-left: 10px;
} /*done*/
.margin-horizontal {
  margin-left: 10px;
  margin-right: 10px;
} /*done*/
.margin-vertical {
  margin-top: 10px;
  margin-bottom: 10px;
} /*done*/
.margin-all {
  margin: 10px;
} /*done*/
.no-margin {
  margin: 0px;
} /*done*/

.no-vertical-margin {
  margin-top: 0px;
  margin-bottom: 0px;
}
.no-horizontal-margin {
  margin-left: 0px;
  margin-right: 0px;
}

.inside-col-shrink {
  margin: 0px 20px;
} /*done - For the inside sections that has also Title section*/
/* Margin section */

hr {
  margin: 0px;
  padding: 0px;
  border-top: 1px dashed #999;
}
/*--------------------------------------------FrameWork------------------------*/
</style>


