 <template>
 
  <v-container fluid id="bg">
      <v-layout  column>
            <v-flex fluid id  xs12 xl3 lg3 md4>
                
                <h3 class="mb-3">HOME FRAGRANCES</h3>
                <span class="mb-3">+45 91 85 17 31 <br> INFO@HOMEFRAGRANCES@GMAIL.COM <br> DÆMNINGEN 35A <br> 7100 VEJLE</span>
                
            </v-flex>
            
        </v-layout>
        <hr class="mb-1">
        <v-layout>
            <v-dialog
      v-model="dialog"
      width="500">
      <template v-slot:activator="{ on }">
        <v-btn flat color="blue" id="privacy"
          v-on="on">Privacy Policy
        </v-btn>
        
      </template>

      <v-card>
        <v-card-title
          class="headline blue lighten-2 white--text"
          primary-title >
          Privacy Policy
        </v-card-title>
        <v-card-text>
We may collect other information that cannot be readily used to identify you,
 such as (for example) the domain name and IP address of your computer. We may use
  this information, individually or in the aggregate, for technical administration
   of our Web site(s); research and development; customer- and account administration;
    and to help us focus our marketing efforts more precisely.
Cookies
Company Name uses “cookies” to store personal data on your computer. 
We may also link information stored on your computer in cookies with 
personal data about specific individuals stored on our servers. 
If you set up your Web browser (for example, Internet Explorer or Firefox) 
so that cookies are not allowed, you might not be able to use some or 
all of the features of our Web site(s).

External data storage sites
We may store your data on servers provided by third party hosting 
vendors with whom we have contracted.

Your privacy responsibilities
To help protect your privacy, be sure:

not to share your user ID or password with anyone else;
to log off the Company Name Web site when you are finished;
to take customary precautions to guard against “malware” (
    viruses, Trojan horses, bots, etc.), for example by installing and updating suitable anti-virus software.
Notice to European Union users
Company Name‘s operations are located primarily in the United States. 
If you provide information to us, the information will be transferred out
 of the European Union (EU) to the United States. By providing personal
  information to us, you are consenting to its storage and use as described herein.

Information collected from children
You must be at least 13 years old to use Company Name‘s Web site(s) 
and service(s). Company Name does not knowingly collect information from
 children under 13. (See the U.S. Children’s Online Privacy Protection Act.)
        </v-card-text>

        <v-divider></v-divider>

        <v-card-actions>
          <v-spacer></v-spacer>
          <v-btn
            color="primary"
            flat
            @click="dialog = false"
          >
            I accept
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
 >
            <v-spacer></v-spacer>
          	  <span>&copy;Designed by Ugne &nbsp; 2019</span>
      </v-layout>
   <!-- 
      <cookie-consent/>
      -->
  </v-container>
  
 </template>


<script>
  export default {
    data () {
      return {
        dialog: false
      }
    }
  }
</script>
 

<style lang="scss" scoped>
//@import "./node_modules/vue-cookieconsent-component/src/scss/cookie-consent";
//@import "./node_modules/vue-cookieconsent-component/src/scss/cookie-consent-bottom";
//@import "./node_modules/vue-cookieconsent-component/src/scss/cookie-consent-transition";
#bg {
background-color: rgb(231, 231, 231);
}
h3{
font-size: 25.5px;
  font-weight: 600;
  line-height: normal;
  letter-spacing: 2px;
  color: #161616;
  text-transform: uppercase;
}
hr {
    color: #1a1a1a;
}
a {font-size: 18px;
  font-weight: normal;
  font-style: normal;
  font-stretch: normal;
  line-height: 1.5;
  letter-spacing: normal;
  color: #181818;
  text-decoration: none;
 }
 p {font-size: 18px;
  font-weight: normal;
  font-style: normal;
  font-stretch: normal;
  line-height: 1.5;
  letter-spacing: normal;
  color: #161616;
  text-decoration: none;
 }
 span {
   font-weight: normal;
  font-style: normal;
  font-stretch: normal;
  line-height: 1.5;
  letter-spacing: normal;
  color: rgb(20, 20, 20);
  text-decoration: none;
  font-size: 14px;
  font-weight: 200;
  
 }
</style>