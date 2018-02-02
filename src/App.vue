<template>
  <!-- Don't drop "q-app" class -->
  <div id="q-app">

    <q-layout ref="layout" view="hHh lPr lFr">
      <q-toolbar slot="header" class="custom-theme-color">

        <q-toolbar-title class="text-center">
          BIR Tax Calculator
        </q-toolbar-title>

        <!--<q-btn flat>
          <q-icon name="menu" />
        </q-btn>-->

      </q-toolbar>

      <q-tabs slot="navigation" v-model="selectedTab">

        <!-- Tabs -->
        <q-tab slot="title" name="daily-tab" @select="switchTab" default>Daily</q-tab>
        <q-tab slot="title" name="weekly-tab" @select="switchTab">Weekly</q-tab>
        <q-tab slot="title" name="semi-monthly-tab" @select="switchTab">Semi-Monthly</q-tab>
        <q-tab slot="title" name="monthly-tab" @select="switchTab">Monthly</q-tab>

        <!-- Daily Tab -->
        <q-tab-pane name="daily-tab">
            <q-scroll-area style="width: 100%; height: 330px;">
          <q-input v-model="displayAmount" type="tel" prefix="₱ " :error="error" :stack-label="error ? 'Invalid Amount' : 'Enter Amount'" @change="computeTakeHomePay" clearable/>

          <q-list>
            <q-item>

              <q-item-main>
                <q-item-tile label>Withholding Tax</q-item-tile>
                <q-item-tile sublabel>{{displayTotalTax}}</q-item-tile>
              </q-item-main>

            </q-item>

            <q-item-separator />

            <q-item>

              <q-item-main>
                <q-item-tile label>Net Pay</q-item-tile>
                <q-item-tile sublabel>{{displayNetPay}}</q-item-tile>
              </q-item-main>

            </q-item>

          </q-list>
            </q-scroll-area>
        </q-tab-pane>

        <!-- Weekly Tab -->
        <q-tab-pane name="weekly-tab">
            <q-scroll-area style="width: 100%; height: 330px;">
          <q-input v-model="displayAmount" type="tel" prefix="₱ " :error="error" :stack-label="error ? 'Invalid Amount' : 'Enter Amount'" @change="computeTakeHomePay" clearable/>

          <q-list>
            <q-item>

              <q-item-main>
                <q-item-tile label>Withholding Tax</q-item-tile>
                <q-item-tile sublabel>{{displayTotalTax}}</q-item-tile>
              </q-item-main>

            </q-item>

            <q-item-separator />

            <q-item>

              <q-item-main>
                <q-item-tile label>Net Pay</q-item-tile>
                <q-item-tile sublabel>{{displayNetPay}}</q-item-tile>
              </q-item-main>

            </q-item>

          </q-list>
            </q-scroll-area>
        </q-tab-pane>

        <!-- Semi Monthly Tab -->
        <q-tab-pane name="semi-monthly-tab">
            <q-scroll-area style="width: 100%; height: 330px;">
          <q-input v-model="displayAmount" type="tel" prefix="₱ " :error="error" :stack-label="error ? 'Invalid Amount' : 'Enter Amount'" @change="computeTakeHomePay" clearable/>

          <q-list>
            <q-item>

              <q-item-main>
                <q-item-tile label>Withholding Tax</q-item-tile>
                <q-item-tile sublabel>{{displayTotalTax}}</q-item-tile>
              </q-item-main>

            </q-item>

            <q-item-separator />

            <q-item>

              <q-item-main>
                <q-item-tile label>Net Pay</q-item-tile>
                <q-item-tile sublabel>{{displayNetPay}}</q-item-tile>
              </q-item-main>

            </q-item>

          </q-list>
            </q-scroll-area>
        </q-tab-pane>

        <!-- Monthly Tab -->
        <q-tab-pane name="monthly-tab">

          <q-input v-model="displayAmount" type="tel" prefix="₱ " :error="error" :stack-label="error ? 'Invalid Amount' : 'Enter Amount'" @change="computeTakeHomePay" clearable/>

          <q-list highlight>

            <q-item>

              <q-item-main>
                <q-item-tile label>SSS</q-item-tile>
                <q-item-tile sublabel>{{displaySSS}}</q-item-tile>
              </q-item-main>

            </q-item>

            <q-item-separator />

            <q-item>

              <q-item-main>
                <q-item-tile label>PhilHealth</q-item-tile>
                <q-item-tile sublabel>{{displayPhilHealth}}</q-item-tile>
              </q-item-main>

            </q-item>

            <q-item-separator />

            <q-item>

              <q-item-main>
                <q-item-tile label>Pag-Ibig</q-item-tile>
                <q-item-tile sublabel>{{displayPagIbig}}</q-item-tile>
              </q-item-main>

            </q-item>

            <q-item-separator />

            <q-item>

              <q-item-main>
                <q-item-tile label>Withholding Tax</q-item-tile>
                <q-item-tile sublabel>{{displayTotalTax}}</q-item-tile>
              </q-item-main>

            </q-item>

            <q-item-separator />

            <q-item>

              <q-item-main>
                <q-item-tile label>Total Deduction</q-item-tile>
                <q-item-tile sublabel>{{displayTotalDeduction}}</q-item-tile>
              </q-item-main>

            </q-item>

            <q-item-separator />

            <q-item>

              <q-item-main>
                <q-item-tile label>Net Pay</q-item-tile>
                <q-item-tile sublabel>{{displayNetPay}}</q-item-tile>
              </q-item-main>

            </q-item>

          </q-list>

        </q-tab-pane>

      </q-tabs>
    </q-layout>

  </div>
</template>

<script>

    import { QTabs, QTab, QBtn, QInput, QRouteTab, QTabPane, QToolbar, QToolbarTitle, QLayout, QIcon, QSpinnerHourglass, QList, QListHeader, QItem, QItemSide, QItemMain, QItemTile, QItemSeparator, Toast, QScrollArea  } from 'quasar'

    var admobid = {};

    export default {
        components: {
            QTabs,
            QTab,
            QBtn,
            QInput,
            QRouteTab,
            QTabPane,
            QToolbar,
            QToolbarTitle,
            QLayout,
            QIcon,
            QSpinnerHourglass,
            QList,
            QListHeader,
            QItem,
            QItemSide,
            QItemMain,
            QItemTile,
            QItemSeparator,
            Toast,
            QScrollArea
        },
        data () {
            return {
                selectedTab: 'daily-tab',
                amount: 0,
                result: 0,
                taxableAmount: 0,
                baseWithholdingTax: 0,
                additionalTax: 0,
                totalTax: 0,
                deductPhilHealth: 0,
                deductSSS: 0,
                deductPagIbig: 0,
                totalDeduction: 0,
                error: false,
                adsShown: false
            }
        },
        created() {
            /*admob.initAdmob("ca-app-pub-9675873595337521/7000001749","ca-app-pub-9675873595337521/7940057636");

            var admobParam=new admob.Params();
            admobParam.isTesting=false;
            admob.showBanner(admob.BannerSize.BANNER,admob.Position.BOTTOM_CENTER,admobParam);
*/
            admobid = {
                banner: 'ca-app-pub-1165380004069778/4879259619',
                interstitial: 'ca-app-pub-1165380004069778/2997780853'
            };

            if(AdMob) AdMob.createBanner({
                adId: admobid.banner,
                position: AdMob.AD_POSITION.BOTTOM_CENTER,
                autoShow: true });

            if(AdMob) AdMob.prepareInterstitial( {adId:admobid.interstitial, autoShow:false} );

        },
        methods: {
            switchTab () {
                // show the interstitial later, e.g. at end of game level
                if(!this.adsShown) {
                    if(AdMob) AdMob.showInterstitial();
                    this.adsShown = true;
                }

                this.amount = 0;
                this.result = 0;
                this.totalDeduction = 0;
                this.totalTax = 0;
                this.deductPhilHealth = 0;
                this.deductSSS = 0;
                this.deductPagIbig = 0;

            },
            computeTakeHomePay (event, done) {

                var regexp = /^(\d{1,8})(\.\d{0,8})?$/g;

                if (!regexp.test(this.amount)) {

                    Toast.create.negative('Please enter a valid amount.')
                    this.result = 0;
                    this.totalDeduction = 0;
                    this.totalTax = 0;
                    this.deductPhilHealth = 0;
                    this.deductSSS = 0;
                    this.deductPagIbig = 0;
                    this.error = true;
                    return

                } else {

                    this.error = false;

                    if(this.selectedTab === 'daily-tab') {

                        this.taxableAmount = this.amount;

                        if(this.taxableAmount <= 685) {
                            this.baseWithholdingTax = 0;
                            this.additionalTax = 0;
                        } else if(this.taxableAmount > 685 && this.taxableAmount <= 1096) {
                            this.baseWithholdingTax = 0;
                            this.additionalTax = (this.taxableAmount - 685) * 0.20;
                        } else if(this.taxableAmount > 1096 && this.taxableAmount <= 2192) {
                            this.baseWithholdingTax = 82.19;
                            this.additionalTax = (this.taxableAmount - 1096) * 0.25;
                        } else if(this.taxableAmount > 2192 && this.taxableAmount <= 5479) {
                            this.baseWithholdingTax = 356.16;
                            this.additionalTax = (this.taxableAmount - 2192) * 0.30;
                        } else if(this.taxableAmount > 5479 && this.taxableAmount <= 21918) {
                            this.baseWithholdingTax = 1342.47;
                            this.additionalTax = (this.taxableAmount - 5479) * 0.32;
                        } else if(this.taxableAmount > 21918) {
                            this.baseWithholdingTax = 6602.74;
                            this.additionalTax = (this.taxableAmount - 21918) * 0.35;
                        }

                    } else if(this.selectedTab === 'weekly-tab') {

                        this.taxableAmount = this.amount;

                        if(this.taxableAmount <= 4808) {
                            this.baseWithholdingTax = 0;
                            this.additionalTax = 0;
                        } else if(this.taxableAmount > 4808 && this.taxableAmount <= 7692) {
                            this.baseWithholdingTax = 0;
                            this.additionalTax = (this.taxableAmount - 4808) * 0.20;
                        } else if(this.taxableAmount > 7692 && this.taxableAmount <= 15385) {
                            this.baseWithholdingTax = 576.92;
                            this.additionalTax = (this.taxableAmount - 7692) * 0.25;
                        } else if(this.taxableAmount > 15385 && this.taxableAmount <= 38462) {
                            this.baseWithholdingTax = 2500;
                            this.additionalTax = (this.taxableAmount - 15385) * 0.30;
                        } else if(this.taxableAmount > 38462 && this.taxableAmount <= 153846) {
                            this.baseWithholdingTax = 9423.08;
                            this.additionalTax = (this.taxableAmount - 38462) * 0.32;
                        } else if(this.taxableAmount > 153846) {
                            this.baseWithholdingTax = 46346.15;
                            this.additionalTax = (this.taxableAmount - 153846) * 0.35;
                        }

                    } else if(this.selectedTab === 'semi-monthly-tab') {

                        this.taxableAmount = this.amount;

                        if(this.taxableAmount <= 10417) {
                            this.baseWithholdingTax = 0;
                            this.additionalTax = 0;
                        } else if(this.taxableAmount > 10417 && this.taxableAmount <= 16667) {
                            this.baseWithholdingTax = 0;
                            this.additionalTax = (this.taxableAmount - 10417) * 0.20;
                        } else if(this.taxableAmount > 16667 && this.taxableAmount <= 33333) {
                            this.baseWithholdingTax = 1250;
                            this.additionalTax = (this.taxableAmount - 16667) * 0.25;
                        } else if(this.taxableAmount > 33333 && this.taxableAmount <= 83333) {
                            this.baseWithholdingTax = 5416.67;
                            this.additionalTax = (this.taxableAmount - 33333) * 0.30;
                        } else if(this.taxableAmount > 83333 && this.taxableAmount <= 333333) {
                            this.baseWithholdingTax = 20416.67;
                            this.additionalTax = (this.taxableAmount - 83333) * 0.32;
                        } else if(this.taxableAmount > 333333) {
                            this.baseWithholdingTax = 100416.67;
                            this.additionalTax = (this.taxableAmount - 333333) * 0.35;
                        }

                    } else if(this.selectedTab === 'monthly-tab') {

                        this.deductPagIbig = 100;

                        if(this.amount <= 10000) {
                            this.deductPhilHealth = 137.50;
                        } else if(this.amount > 10000 && this.amount < 40000) {
                            this.deductPhilHealth = (this.amount * 0.0275)/2;
                        } else if(this.amount >= 40000) {
                            this.deductPhilHealth = 550;
                        }

                        if(this.amount >= 1000 && this.amount <= 1249.99) {
                            this.deductSSS = 36.30;
                        } else if(this.amount >= 1250 && this.amount <= 1749.99) {
                            this.deductSSS = 54.50;
                        } else if(this.amount >= 1750 && this.amount <= 2249.99) {
                            this.deductSSS = 72.70;
                        } else if(this.amount >= 2250 && this.amount <= 2749.99) {
                            this.deductSSS = 90.80;
                        } else if(this.amount >= 2750 && this.amount <= 3249.99) {
                            this.deductSSS = 109;
                        } else if(this.amount >= 3250 && this.amount <= 3749.99) {
                            this.deductSSS = 127.20;
                        } else if(this.amount >= 3750 && this.amount <= 4249.99) {
                            this.deductSSS = 145.30;
                        } else if(this.amount >= 4250 && this.amount <= 4749.99) {
                            this.deductSSS = 163.50;
                        } else if(this.amount >= 4750 && this.amount <= 5249.99) {
                            this.deductSSS = 181.70;
                        } else if(this.amount >= 5250 && this.amount <= 5749.99) {
                            this.deductSSS = 199.80;
                        } else if(this.amount >= 5750 && this.amount <= 6249.99) {
                            this.deductSSS = 218;
                        } else if(this.amount >= 6250 && this.amount <= 6749.99) {
                            this.deductSSS = 236.20;
                        } else if(this.amount >= 6750 && this.amount <= 7249.99) {
                            this.deductSSS = 254.30;
                        } else if(this.amount >= 7250 && this.amount <= 7749.99) {
                            this.deductSSS = 272.50;
                        } else if(this.amount >= 7750 && this.amount <= 8249.99) {
                            this.deductSSS = 290.70;
                        } else if(this.amount >= 8250 && this.amount <= 8749.99) {
                            this.deductSSS = 308.80;
                        } else if(this.amount >= 8750 && this.amount <= 9249.99) {
                            this.deductSSS = 327;
                        } else if(this.amount >= 9250 && this.amount <= 9749.99) {
                            this.deductSSS = 345.20;
                        } else if(this.amount >= 9750 && this.amount <= 10249.99) {
                            this.deductSSS = 363.30;
                        } else if(this.amount >= 10250 && this.amount <= 10749.99) {
                            this.deductSSS = 381.50;
                        } else if(this.amount >= 10750 && this.amount <= 11249.99) {
                            this.deductSSS = 399.70;
                        } else if(this.amount >= 11250 && this.amount <= 11749.99) {
                            this.deductSSS = 417.80;
                        } else if(this.amount >= 11750 && this.amount <= 12249.99) {
                            this.deductSSS = 436;
                        } else if(this.amount >= 12250 && this.amount <= 12749.99) {
                            this.deductSSS = 454.20;
                        } else if(this.amount >= 12750 && this.amount <= 13249.99) {
                            this.deductSSS = 472.30;
                        } else if(this.amount >= 13250 && this.amount <= 13749.99) {
                            this.deductSSS = 490.50;
                        } else if(this.amount >= 13750 && this.amount <= 14249.99) {
                            this.deductSSS = 508.70;
                        } else if(this.amount >= 14250 && this.amount <= 14749.99) {
                            this.deductSSS = 526.80;
                        } else if(this.amount >= 14750 && this.amount <= 15249.99) {
                            this.deductSSS = 545;
                        } else if(this.amount >= 15250 && this.amount <= 15749.99) {
                            this.deductSSS = 563.20;
                        } else if(this.amount >= 15750) {
                            this.deductSSS = 581.30;
                        }

                        this.taxableAmount = this.amount - (this.deductPagIbig + this.deductPhilHealth + this.deductSSS);

                        if(this.taxableAmount <= 20833) {
                            this.baseWithholdingTax = 0;
                            this.additionalTax = 0;
                        } else if(this.taxableAmount > 20833 && this.taxableAmount <= 33333) {
                            this.baseWithholdingTax = 0;
                            this.additionalTax = (this.taxableAmount - 20833) * 0.20;
                        } else if(this.taxableAmount > 33333 && this.taxableAmount <= 66667) {
                            this.baseWithholdingTax = 2500;
                            this.additionalTax = (this.taxableAmount - 33333) * 0.25;
                        } else if(this.taxableAmount > 66667 && this.taxableAmount <= 166667) {
                            this.baseWithholdingTax = 10833.33;
                            this.additionalTax = (this.taxableAmount - 66667) * 0.30;
                        } else if(this.taxableAmount > 166667 && this.taxableAmount <= 666667) {
                            this.baseWithholdingTax = 40833.33;
                            this.additionalTax = (this.taxableAmount - 166667) * 0.32;
                        } else if(this.taxableAmount > 666667) {
                            this.baseWithholdingTax = 200833.33;
                            this.additionalTax = (this.taxableAmount - 666667) * 0.35;
                        }

                    }

                    this.totalTax = this.baseWithholdingTax + this.additionalTax;
                    this.totalDeduction = (this.amount - this.taxableAmount) + this.totalTax;
                    this.result = this.taxableAmount - this.totalTax;

                }
            }
        },
        computed: {
            displaySSS: function () {
                return '₱ ' + this.deductSSS.toFixed(2).toString().replace(/\B(?=(\d{3})+(?!\d))/g, ",");
            },
            displayPhilHealth: function () {
                return '₱ ' + this.deductPhilHealth.toFixed(2).toString().replace(/\B(?=(\d{3})+(?!\d))/g, ",");
            },
            displayPagIbig: function () {
                return '₱ ' + this.deductPagIbig.toFixed(2).toString().replace(/\B(?=(\d{3})+(?!\d))/g, ",");
            },
            displayTotalTax: function () {
                return '₱ ' + this.totalTax.toFixed(2).toString().replace(/\B(?=(\d{3})+(?!\d))/g, ",");
            },
            displayTotalDeduction: function () {
                return '₱ ' + this.totalDeduction.toFixed(2).toString().replace(/\B(?=(\d{3})+(?!\d))/g, ",");
            },
            displayNetPay: function () {
                return '₱ ' + this.result.toFixed(2).toString().replace(/\B(?=(\d{3})+(?!\d))/g, ",");
            },
            displayAmount: {
            	get: function () {
	            	if(this.amount) {
	            		return this.amount;
	            	} else {
	            		return '';
            		}
		        },
		        set: function (newValue) {

                    this.amount = newValue;
		        }
            }
        }
    }
</script>

<style>
    .custom-theme-color {
        background-color: #4caf50;
    }

    .q-tabs-head {
        background-color: #4caf50;
    }

</style>