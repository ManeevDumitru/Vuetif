<script>
  /* eslint-disable */
  export default {
    data: () => ({
      defaultCountry: "United States",
      applicationCountries: ["United States", "Australia", "Canada"],
      footerCategories: [
        {
          name: "About Us",
          links: [
            {
              name: "How It Works",
              link: ""
            },
            {
              name: "Why Choose Us",
              link: ""
            },
            {
              name: "Privacy Statement",
              link: ""
            },
            {
              name: "Compliance Policy",
              link: ""
            },
            {
              name: "Terms of Service",
              link: ""
            },
          ]
        },
        {
          name: "FAQ",
          links: [
            {
              name: "Fees & Services",
              link: ""
            },
            {
              name: "Membership System",
              link: ""
            },
            {
              name: "International Delivery",
              link: ""
            },
            {
              name: "Couriers & Services",
              link: ""
            },
            {
              name: "Shipping Category",
              link: ""
            },
            {
              name: "Site Map",
              link: ""
            },
          ]
        },
        {
          name: "Help",
          links: [
            {
              name: "FAQ",
              link: ""
            },
            {
              name: "Contact Us",
              link: ""
            },
            {
              name: "About Us",
              link: ""
            },
          ]
        },
      ],
      date: '',
      menu: false,
      popupVisible: true,
      jobApplication: false,
      createAccount: false,
      resumeUpload: false,
      years: [1900, 1901, 1902],
      months: ["Jan", "Feb", "Mar", "Apr", "May", "Jun", "Jul", "Aug"],
      days: [1, 2, 3, 4, 5, 6, 7, 8, 9, 10],
      time: ["am", "pm"]
    }),
    computed: {
      computedDate() {
        return this.date ? moment(this.date).format('dddd, MMMM Do YYYY') : ''
      },
    },
    methods: {
      switchForms(form) {
        switch (form) {
          case("jobApplication"):
            this.popupVisible = false;
            setTimeout(() => this.jobApplication = true, 1000);
            break;
          case('resumeUpload'):
            this.popupVisible = false;
            setTimeout(() => this.resumeUpload = true, 1000);

            break;
          case("createAccount"):
            this.jobApplication = false;
            this.resumeUpload = false;
            setTimeout(() => this.createAccount = true, 1000);
            break;
          case("reset"):
            this.popupVisible = true;
            this.createAccount = false;
            this.jobApplication = false;
            this.resumeUpload = false;
            break;
        }
        console.log(this.jobApplication);
      }
    }
  };
</script>

<template>
  <v-app>
    <v-card>
      <v-app-bar
        color="white"
        flat
        app
      >
        <a href="">
          <img src="http://thatdeliveryplace.com/resources/Images/en/www/indexnew/logo.png" alt="Delivery Place">
        </a>
        <v-spacer/>
        <v-menu open-on-hover offset-y>
          <template v-slot:activator="{ on }">
            <div
              v-on="on"
              class="black--text font-weight-light title"
              style="height: 60px; line-height: 60px"
            >
              Help center
              <v-icon class="mr-5" size="12px" style="transform: rotate(180deg)">
                mdi-triangle
              </v-icon>
            </div>
          </template>
          <v-list dense>
            <v-list-item class="text-center">
              <v-list-item-content>
                Contact us
              </v-list-item-content>
            </v-list-item>
            <v-list-item>
              <v-list-item-content class="text-center">
                About us
              </v-list-item-content>
            </v-list-item>
          </v-list>
        </v-menu>
        <a href="" class="mr-10 black--text font-weight-light title">
          How it works
        </a>
      </v-app-bar>
    </v-card>
    <div style="width: 100%; height: 100%">
      <transition name="fade_out_popup">
        <div v-if="popupVisible">
          <div
            style="width: 400px; position: absolute; left: 50%; top: 50%; transform: translate(-50%, -75%)"
            class="text-center">
            <div class="display-1 mb-5 font-weight-bold">
              Your country
            </div>
            <template>
              <v-divider/>
            </template>
            <div class="pa-5">
              <v-select
                v-model="defaultCountry"
                :items="applicationCountries"
              />
              <div>
                <v-btn
                  width="100%"
                  height="50px"
                  depressed
                  color="#0066CC"
                  class="white--text headline"
                  @click="switchForms('jobApplication')"
                >
                  Fill in Job Application
                </v-btn>
              </div>
              <div>
                <v-btn
                  width="100%"
                  height="50px"
                  class="mt-10 white--text headline"
                  depressed
                  color="#0066CC"
                  @click="switchForms('resumeUpload')"
                >
                  Upload Your Resume
                </v-btn>
              </div>
            </div>
          </div>
        </div>
      </transition>
      <transition name="fade_job_application">
        <div v-if="jobApplication">
          <div
            style="width: 1200px; margin: 120px auto">
            <div>
              <v-row>
                <v-col
                  class="text-center font-weight-bold headline"
                  cols="12">
                  Job Application Form
                </v-col>
              </v-row>
              <v-divider/>
              <v-row class="simpleRow" dense>
                <v-col cols="4">
                  <div class="d-flex">
                    <v-col cols="6" class="form_cat">
                      First Name
                    </v-col>
                    <v-text-field/>
                  </div>
                </v-col>
                <v-col cols="4">
                  <div class="d-flex">
                    <v-col cols="6" class="form_cat">
                      Middle Name
                    </v-col>
                    <v-text-field/>
                  </div>
                </v-col>
                <v-col cols="4">
                  <div class="d-flex">
                    <v-col cols="6" class="form_cat">
                      Last Name
                    </v-col>
                    <v-text-field/>
                  </div>
                </v-col>
              </v-row>
              <v-row class="simpleRow" dense>
                <v-col cols="6">
                  <div class="d-flex">
                    <v-col cols="4" class="form_cat">
                      Mailing Adress
                    </v-col>
                    <v-text-field/>
                  </div>
                </v-col>
                <v-col cols="5">
                  <div class="d-flex">
                    <v-col cols="5" class="form_cat">
                      APT/UNIT
                    </v-col>
                    <v-text-field></v-text-field>
                  </div>
                </v-col>
              </v-row>
              <v-row class="simpleRow" dense>
                <v-col cols="4">
                  <div class="d-flex">
                    <v-col cols="6" class="form_cat">
                      State
                    </v-col>
                    <v-text-field/>
                  </div>
                </v-col>
                <v-col cols="4">
                  <div class="d-flex">
                    <v-col cols="6" class="form_cat">
                      ZIP Code
                    </v-col>
                    <v-text-field/>
                  </div>
                </v-col>
                <v-col cols="4">
                  <div class="d-flex">
                    <v-col cols="6" class="form_cat">
                      City
                    </v-col>
                    <v-text-field/>
                  </div>
                </v-col>
              </v-row>
              <v-row class="simpleRow" dense>
                <v-col cols="4">
                  <div class="d-flex">
                    <v-col cols="6" class="form_cat">
                      Cell Phone
                    </v-col>
                    <v-text-field/>
                  </div>
                </v-col>
                <v-col cols="4">
                  <div class="d-flex">
                    <v-col cols="6" class="form_cat">
                      Home Phone
                    </v-col>
                    <v-text-field/>
                  </div>
                </v-col>
              </v-row>
              <v-row class="tallRow" dense>
                <v-col cols="6">
                  <div class="d-flex">
                    <v-col cols="4" class="form_cat" style="line-height: 65px !important;">
                      Date of birth
                    </v-col>
                    <v-row cols="12">
                      <v-col>
                        <v-select
                          placeholder="Year"
                          :items="years"
                        />
                      </v-col>
                      <v-col>
                        <v-select
                          placeholder="Month"
                          :items="months"
                        />
                      </v-col>
                      <v-col>
                        <v-select
                          placeholder="Day"
                          :items="days"
                        />
                      </v-col>
                    </v-row>
                  </div>
                </v-col>
                <v-col cols="5">
                  <div class="d-flex">
                    <v-col cols="6" class="font-weight-bold text-right title form_cat_two_lines">
                      Dates available for work
                    </v-col>
                    <v-menu
                      ref="menu"
                      v-model="menu"
                      :close-on-content-click="false"
                      :return-value.sync="date"
                      transition="scale-transition"
                      offset-y
                      min-width="290px"
                    >
                      <template v-slot:activator="{ on }">
                        <v-text-field
                          v-model="date"
                          v-on="on"
                        ></v-text-field>
                      </template>
                      <v-date-picker v-model="date" no-title scrollable>
                        <v-spacer></v-spacer>
                        <v-btn text color="primary" @click="menu = false">Cancel</v-btn>
                        <v-btn text color="primary" @click="$refs.menu.save(date)">OK</v-btn>
                      </v-date-picker>
                    </v-menu>
                  </div>
                </v-col>
              </v-row>
              <v-row class="tallRow" dense>
                <v-col cols="6">
                  <div class="d-flex">
                    <v-col cols="4" class="form_cat">
                      Were you referred
                    </v-col>
                    <v-text-field/>
                  </div>
                </v-col>
                <v-col cols="6">
                  <div class="d-flex">
                    <v-col cols="4" class="form_cat_two_lines">
                      How did you hear about this job?
                    </v-col>
                    <v-text-field/>
                  </div>
                </v-col>
              </v-row>
            </div>
            <div class="mt-6">
              <v-row>
                <v-col
                  class="text-center font-weight-bold headline"
                  cols="12">
                  Additional employment history (optional)
                </v-col>
              </v-row>
              <v-divider/>
              <v-row style="height: 75px" dense>
                <v-col cols="6">
                  <div class="d-flex">
                    <v-col cols="4" class="form_cat">
                      Company name:
                    </v-col>
                    <v-text-field/>
                  </div>
                </v-col>
                <v-col cols="6">
                  <div class="d-flex">
                    <v-col cols="4" class="form_cat_two_lines">
                      Employers phone:
                    </v-col>
                    <v-text-field/>
                  </div>
                </v-col>
              </v-row>
              <v-row style="height: 55px" dense>
                <v-col cols="4">
                  <div class="d-flex">
                    <v-col cols="6" class="form_cat">
                      Adress:
                    </v-col>
                    <v-text-field/>
                  </div>
                </v-col>
                <v-col cols="4">
                  <div class="d-flex">
                    <v-col cols="6" class="form_cat">
                      City / State:
                    </v-col>
                    <v-text-field/>
                  </div>
                </v-col>
                <v-col cols="4">
                  <div class="d-flex">
                    <v-col cols="6" class="form_cat">
                      ZIP:
                    </v-col>
                    <v-text-field/>
                  </div>
                </v-col>
              </v-row>
              <v-row style="height: 55px" dense>
                <v-col cols="4">
                  <div class="d-flex">
                    <v-col cols="6" class="form_cat">
                      Job title:
                    </v-col>
                    <v-text-field/>
                  </div>
                </v-col>
                <v-col cols="4">
                  <div class="d-flex">
                    <v-col cols="6" class="form_cat">
                      Employed from:
                    </v-col>
                    <v-text-field/>
                  </div>
                </v-col>
                <v-col cols="4">
                  <div class="d-flex">
                    <v-col cols="6" class="form_cat">
                      Employed to:
                    </v-col>
                    <v-text-field/>
                  </div>
                </v-col>
              </v-row>
              <v-row style="height: 55px" dense>
                <v-col cols="4">
                  <div class="d-flex">
                    <v-col cols="6" class="form_cat">
                      Starting salary:
                    </v-col>
                    <v-text-field/>
                  </div>
                </v-col>
                <v-col cols="4">
                  <div class="d-flex">
                    <v-col cols="6" class="form_cat">
                      Ending salary:
                    </v-col>
                    <v-text-field/>
                  </div>
                </v-col>
                <v-col cols="4">
                  <div class="d-flex">
                    <v-col cols="6" class="form_cat">
                      Supervisor`s name:
                    </v-col>
                    <v-text-field/>
                  </div>
                </v-col>
              </v-row>
              <v-row style="height: 55px" dense>
                <v-col cols="12">
                  <div class="d-flex">
                    <v-col cols="2" class="form_cat">
                      Job duties:
                    </v-col>
                    <v-text-field/>
                  </div>
                </v-col>
              </v-row>
              <v-row style="height: 75px" dense>
                <v-col cols="6">
                  <div class="d-flex">
                    <v-col cols="4" class="form_cat">
                      Reason for leaving:
                    </v-col>
                    <v-text-field/>
                  </div>
                </v-col>
                <v-col cols="6">
                  <div class="d-flex">
                    <v-col cols="4" class="form_cat_two_lines">
                      May we contact this employer:
                    </v-col>
                    <v-text-field/>
                  </div>
                </v-col>
              </v-row>
            </div>
            <v-alert color="#F8F8F8" class="mt-6">
              I certify that the information I have provided in this employment application is accurate and has been
              completed to the best of my knowledge and ability. I understand that any falsification, misrepresentation
              or
              omission in my interviews or any other employment record, will be sufficient reason to deny employment
              and/or may be reason for future dismissal.
              Signature: asdasdasdasdasdadssa
            </v-alert>
            <div class="text-center">
              <v-btn
                width="350px"
                height="50px"
                depressed
                color="#0066CC"
                class="white--text headline"
                @click="switchForms('createAccount')"
              >
                Next
              </v-btn>
            </div>
          </div>
        </div>
      </transition>
      <transition name="fade_resume_upload">
        <div v-if="resumeUpload">
          <div style="width: 1200px; margin: 120px auto 350px auto">
            <div>
              <v-row>
                <v-col
                  class="text-center font-weight-bold headline"
                  cols="12">
                  Job Application Form
                </v-col>
              </v-row>
              <v-divider/>
              <v-row class="simpleRow" dense>
                <v-col cols="4">
                  <div class="d-flex">
                    <v-col cols="6" class="form_cat">
                      First Name
                    </v-col>
                    <v-text-field/>
                  </div>
                </v-col>
                <v-col cols="4">
                  <div class="d-flex">
                    <v-col cols="6" class="form_cat">
                      Middle Name
                    </v-col>
                    <v-text-field/>
                  </div>
                </v-col>
                <v-col cols="4">
                  <div class="d-flex">
                    <v-col cols="6" class="form_cat">
                      Last Name
                    </v-col>
                    <v-text-field/>
                  </div>
                </v-col>
              </v-row>
              <v-row class="simpleRow" dense>
                <v-col cols="6">
                  <div class="d-flex">
                    <v-col cols="4" class="form_cat">
                      Mailing Adress
                    </v-col>
                    <v-text-field/>
                  </div>
                </v-col>
                <v-col cols="5">
                  <div class="d-flex">
                    <v-col cols="5" class="form_cat">
                      APT/UNIT
                    </v-col>
                    <v-text-field></v-text-field>
                  </div>
                </v-col>
              </v-row>
              <v-row class="simpleRow" dense>
                <v-col cols="4">
                  <div class="d-flex">
                    <v-col cols="6" class="form_cat">
                      State
                    </v-col>
                    <v-text-field/>
                  </div>
                </v-col>
                <v-col cols="4">
                  <div class="d-flex">
                    <v-col cols="6" class="form_cat">
                      ZIP Code
                    </v-col>
                    <v-text-field/>
                  </div>
                </v-col>
                <v-col cols="4">
                  <div class="d-flex">
                    <v-col cols="6" class="form_cat">
                      City
                    </v-col>
                    <v-text-field/>
                  </div>
                </v-col>
              </v-row>
              <v-row class="simpleRow" dense>
                <v-col cols="4">
                  <div class="d-flex">
                    <v-col cols="6" class="form_cat">
                      Cell Phone
                    </v-col>
                    <v-text-field/>
                  </div>
                </v-col>
                <v-col cols="4">
                  <div class="d-flex">
                    <v-col cols="6" class="form_cat">
                      Home Phone
                    </v-col>
                    <v-text-field/>
                  </div>
                </v-col>
              </v-row>
              <v-row class="tallRow" dense>
                <v-col cols="6">
                  <div class="d-flex">
                    <v-col cols="4" class="form_cat" style="line-height: 65px !important;">
                      Date of birth
                    </v-col>
                    <v-row cols="12">
                      <v-col>
                        <v-select
                          placeholder="Year"
                          :items="years"
                        />
                      </v-col>
                      <v-col>
                        <v-select
                          placeholder="Month"
                          :items="months"
                        />
                      </v-col>
                      <v-col>
                        <v-select
                          placeholder="Day"
                          :items="days"
                        />
                      </v-col>
                    </v-row>
                  </div>
                </v-col>
                <v-col cols="5">
                  <div class="d-flex">
                    <v-col cols="6" class="font-weight-bold text-right title form_cat_two_lines">
                      Dates available for work
                    </v-col>
                    <v-menu
                      ref="menu"
                      v-model="menu"
                      :close-on-content-click="false"
                      :return-value.sync="date"
                      transition="scale-transition"
                      offset-y
                      min-width="290px"
                    >
                      <template v-slot:activator="{ on }">
                        <v-text-field
                          v-model="date"
                          v-on="on"
                        ></v-text-field>
                      </template>
                      <v-date-picker v-model="date" no-title scrollable>
                        <v-spacer></v-spacer>
                        <v-btn text color="primary" @click="menu = false">Cancel</v-btn>
                        <v-btn text color="primary" @click="$refs.menu.save(date)">OK</v-btn>
                      </v-date-picker>
                    </v-menu>
                  </div>
                </v-col>
              </v-row>
              <v-row class="tallRow" dense>
                <v-col cols="6">
                  <div class="d-flex">
                    <v-col cols="4" class="form_cat">
                      Were you referred
                    </v-col>
                    <v-text-field/>
                  </div>
                </v-col>
                <v-col cols="6">
                  <div class="d-flex">
                    <v-col cols="4" class="form_cat_two_lines">
                      How did you hear about this job?
                    </v-col>
                    <v-text-field/>
                  </div>
                </v-col>
              </v-row>
              <v-row class="simpleRow" dense>
                <v-col cols="4">
                  <div class="d-flex">
                    <v-col cols="6" class="form_cat">
                      Upload resume:
                    </v-col>
                    <template>
                      <v-file-input accept="image/*" label="File input"></v-file-input>
                    </template>
                  </div>
                </v-col>
              </v-row>
            </div>
            <v-alert color="#F8F8F8" class="mt-5">
              I certify that the information I have provided in this employment application is accurate and has been
              completed to the best of my knowledge and ability. I understand that any falsification, misrepresentation
              or
              omission in my interviews or any other employment record, will be sufficient reason to deny employment
              and/or may be reason for future dismissal.
              Signature: asdasdasdasdasdadssa
            </v-alert>
            <div class="text-center">
              <v-btn
                width="350px"
                height="50px"
                depressed
                color="#0066CC"
                class="white--text headline"
                @click="switchForms('createAccount')"
              >
                Next
              </v-btn>
            </div>
          </div>
        </div>
      </transition>
      <transition name="fade_create_account">
        <div v-if="createAccount" style="width: 1200px; margin: 0 auto">
          <div>
            <v-row>
              <v-col
                class="text-center font-weight-bold headline"
                cols="12">
                Create an account
              </v-col>
            </v-row>
            <v-divider/>
            <v-row style="height: 55px" dense>
              <v-col cols="5">
                <div class="d-flex">
                  <v-col cols="5" class="form_cat">
                    First Name:
                  </v-col>
                  <v-text-field/>
                </div>
              </v-col>
              <v-col cols="5">
                <div class="d-flex">
                  <v-col cols="5" class="form_cat">
                    Last Name:
                  </v-col>
                  <v-text-field/>
                </div>
              </v-col>
            </v-row>
            <v-row style="height: 55px" dense>
              <v-col cols="4">
                <div class="d-flex">
                  <v-col cols="6" class="form_cat">
                    E-mail Address:
                  </v-col>
                  <v-text-field/>
                </div>
              </v-col>
              <v-col cols="4">
                <div class="d-flex">
                  <v-col cols="6" class="form_cat">
                    Password:
                  </v-col>
                  <v-text-field/>
                </div>
              </v-col>
              <v-col cols="4">
                <div class="d-flex">
                  <v-col cols="6" class="form_cat">
                    Phone:
                  </v-col>
                  <v-text-field/>
                </div>
              </v-col>
            </v-row>
            <v-row>
              <v-col
                class="text-center font-weight-bold headline"
                cols="12">
                Job application received
              </v-col>
            </v-row>
            <v-row class="px-12">
              Lorem ipsum dolor sit amet, consectetur adipisicing elit. Ab aliquid cum id iure, magnam nemo odit
              officiis,
              praesentium quasi, tempore temporibus ut velit vero voluptas voluptate! Consequuntur deleniti enim
              inventore.
            </v-row>
            <v-row>
              <v-col cols="4">
                <div class="d-flex">
                  <v-col cols="4" class="form_cat" style="line-height: 65px !important;">
                    From:
                  </v-col>
                  <v-row>
                    <v-col>
                      <v-text-field>

                      </v-text-field>
                    </v-col>
                    <v-col>
                      <v-select
                        placeholder="am"
                        :items="time"
                      />
                    </v-col>
                  </v-row>
                </div>
              </v-col>
              <v-col cols="4">
                <div class="d-flex">
                  <v-col cols="4" class="form_cat" style="line-height: 65px !important;">
                    To:
                  </v-col>
                  <v-row>
                    <v-col>
                      <v-text-field>

                      </v-text-field>
                    </v-col>
                    <v-col>
                      <v-select
                        placeholder="am"
                        :items="time"
                      />
                    </v-col>
                  </v-row>
                </div>
              </v-col>
            </v-row>
            <v-row class="text-center">
              <v-col>
                <v-btn
                  width="350px"
                  height="50px"
                  depressed
                  color="#0066CC"
                  class="white--text headline"
                  @click="switchForms('reset')"
                >
                  Next
                </v-btn>
              </v-col>
            </v-row>
          </div>
        </div>
      </transition>
    </div>
    <v-footer
      class="pa-0"
    >
      <div style="width: 100%;">
        <v-row style="max-width: 1200px; margin: auto">
          <v-col
            v-for="footerCategory in footerCategories"
            :key="footerCategory.name"
          >
            <div class="title">
              {{ footerCategory.name }}
            </div>
            <v-divider
              color="black"
              style="width: 100px;"
            />
            <v-list
              color="#F5F5F5"
              dense
            >
              <v-list-item
                class="pa-0"
                v-for="links in footerCategory.links"
                :key="links.name"
              >
                <a
                  href="links.link"
                  class="black--text"
                >
                  {{ links.name }}
                </a>
              </v-list-item>
            </v-list>
          </v-col>
        </v-row>
      </div>
      <v-row class="grey darken-3">
        <v-col class="text-center grey--text">
          &copy 2020
        </v-col>
      </v-row>
    </v-footer>
  </v-app>
</template>

<style scoped>
  * {
    font-family: Arial, Helvetica, sans-serif !important;
  }

  a {
    text-decoration: none;
  }

  header {
    border-bottom: 1px solid grey !important;
  }

  .form_cat {
    font-weight: bold;
    font-size: 18px;
    line-height: 45px;
    text-align: right;
  }

  .form_cat_two_lines {
    line-height: 1.25 !important;
    margin-top: 10px;
    font-size: 18px;
    font-weight: bold;
    text-align: right;
  }

  .v-row .v-col div .v-col:nth-child(2) {
    padding-left: 0 !important;
    padding-right: 0 !important;
  }

  .simpleRow {
    height: 55px !important;
  }

  .tallRow {
    height: 75px !important;
  }

  /* fade transition time */

  .fade_out_popup-enter-active, .fade_out_popup-leave-active,
  .fade_job_application-enter-active, .fade_job_application-leave-active,
  .fade_create_account-enter-active, .fade_create_account-leave-active,
  .fade_resume_upload-enter-active, .fade_resume_upload-leave-active {
    transition: opacity 1s;
  }

  .fade_out_popup-enter, .fade_out_popup-leave-to {
    opacity: 0;
  }

  /* job application */

  .fade_job_application-enter, .fade_job_application-leave-to {
    opacity: 0;
  }

  .fade_job_application-leave, .fade_job_application-enter-to {
    opacity: 1;
  }

  /* resume */

  .fade_resume_upload-enter, .fade_resume_upload-leave-to {
    opacity: 0;
  }

  .fade_resume_upload-enter-to, .fade_resume_upload-leave {
    opacity: 1;
  }

  /* create account */

  .fade_create_account-enter, .fade_create_account-leave-to {
    opacity: 0;
  }

  .fade_create_account-enter-to, .fade_create_account-leave {
    opacity: 1;
  }

</style>
