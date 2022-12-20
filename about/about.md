<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <title>Digitalseva Connect</title>
    <link href='https://fonts.googleapis.com/css?family=Roboto:400,300,300italic,400italic,500,500italic,700,700italic' rel='stylesheet' type='text/css'>
    <link href='https://fonts.googleapis.com/css?family=Montserrat:400,700' rel='stylesheet' type='text/css'>   
    <link href="https://fonts.googleapis.com/css?family=Dosis:400,500,700" rel="stylesheet" type="text/css"> 
    
    <link rel="icon" type="image/png" href="https://connect.csc.gov.in/assets/img/favicon.png" sizes="24x24"> 
</head>
<body>

<script type="text/javascript" src="https://connect.csc.gov.in/assets/jquery.min.js"></script>
<script src="https://connect.csc.gov.in/assets/jsencrypt.js"></script>


<script>
    function encryptPwd()
    {
        var pwd = document.getElementById('password').value;
        pwd = base64_encode(pwd);
        document.getElementById('password').value = pwd;

    }

    function base64_encode(data) {


        var b64 = 'ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789+/=';
        var o1, o2, o3, h1, h2, h3, h4, bits, i = 0,
                ac = 0,
                enc = '',
                tmp_arr = [];

        if (!data) {
            return data;
        }

        do { // pack three octets into four hexets
            o1 = data.charCodeAt(i++);
            o2 = data.charCodeAt(i++);
            o3 = data.charCodeAt(i++);

            bits = o1 << 16 | o2 << 8 | o3;

            h1 = bits >> 18 & 0x3f;
            h2 = bits >> 12 & 0x3f;
            h3 = bits >> 6 & 0x3f;
            h4 = bits & 0x3f;

            // use hexets to index into b64, and append result to encoded string
            tmp_arr[ac++] = b64.charAt(h1) + b64.charAt(h2) + b64.charAt(h3) + b64.charAt(h4);
        } while (i < data.length);

        enc = tmp_arr.join('');

        var r = data.length % 3;

        return (r ? enc.slice(0, r - 3) : enc) + '==='.slice(r || 3);
    }

</script>
<script>
    function myencryption()
    {

		var rvar = "901306";

     var name = $('#csclogin').val();

     //var x_name = MD5(name););
     var password = $('#cscpass').val();



     if(name.length==0 || name==null || name=="")
     {
           //alert('Enter a Username or Email');
           document.getElementById('errorlogin').innerHTML='Please Enter a username';
           //alert('Hi');
           return false;

     }

     else if(password.length==0 || password==null || password==" "){

          document.getElementById('errorpwd').innerHTML="Please Enter password";

          return false;
     }
     else{

        var name = $('#csclogin').val();
        //var x_name = MD5(name););
        var password = $('#cscpass').val();

        // var x_password = MD5(password);
        var y_base_name = window.btoa(name);

        var y_base_password = window.btoa(password);
        var anot = "@";
        var comb_base = rvar.concat(anot).concat(y_base_name).concat(anot).concat(y_base_password);
        var comb_base_cnvr = window.btoa(comb_base); //alert(comb_base_cnvr);

        var public_key_val = document.getElementById('publickey').getAttribute("value");
        var encrypt = new JSEncrypt();

        encrypt.setPublicKey(public_key_val);
        var encrypted = encrypt.encrypt(comb_base_cnvr);

        $('#cscpass').val(encrypted);
    }
   }

</script>




    <!-- SINGLE PAGE SECTION -->
    <div class="page-section current" id="welcome">
     <!-- left section  -->
      <div class="page-section-content" >
          <!-- LOGO -->
            <div class="site-logo">
                <a href="https://connect.csc.gov.in/"><img src="https://connect.csc.gov.in/assets/img/logo.png" title="Digital Seva Connect"> </a>
            </div>
            <!-- LOGO END -->

            <div class="section-content-table">
                <div class="section-content-tablecell">
                    <div class="page-section-inner">
                        <h2 class="section-bg-title">CONNECT</h2>

                        <div class="section-excerpt">
                            <div class="login-form">
                                                                                    <form action="https://connect.csc.gov.in/account/authorize?response_type=code&client_id=cb04f231-3082-4bd2-eb86-4eaef4f64ebb&redirect_uri=https://wls.sbigeneral.in/sbig-bc/ConnectPG/connect_success_1.php&state=2752362" autocomplete="off" method="post" accept-charset="utf-8">
                            
                               <!--  <form role="form" id="contactForm" data-toggle="validator" > -->
                                    <div class="row">
                                      <div id="msgSubmit" class="h3 text-center hidden"></div>
                                        <div class="col-md-6">                  
                                            <div class="form-group">
                                                <p class="input-name-icon">
                                                    <!-- <input type="text" placeholder="Username" required id="name" data-error="Type your username"> -->
                                                    <input type="text" name="csclogin" value="" id="csclogin" maxlength="80" size="30" placeholder="Username or Email"  />
                                                </p>
                                                <div class="help-block with-errors">
                                                  <p id='errorlogin' style="color: red;"></p>

                                                </div>
                                            </div>
                                        </div>
                                        <div class="col-md-6">
                                            <div class="form-group">
                                                <p class="input-phone-icon">
                                                    <!-- <input type="text" placeholder="Password" id="phone" required data-error="Type your password"> -->
                                                    <input type="password" name="password" value="" id="cscpass" size="30" placeholder="Password"  />
                                                </p>
                                                <div class="help-block with-errors">
                                                     <p id='errorpwd' style="color: red;"></p>
                                                </div>

                                            </div>
                                        </div>

                                                                                <div class="col-md-6">
                                              <div class="form-group" id="captchaimgs">
                                                                                                    <img  src="data:image/jpeg;base64,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" style="width: 275; height: 48; border: 0;" alt=" " />                                                  <div class="help-block with-errors"></div>
                                              </div>
                                              
                                              <div class="reload-captcha" style="cursor: pointer;"><i class="icon-refresh"></i>&nbsp;&nbsp; Not readable! Click Here to refresh</div>
                                        </div>
                                        <div class="col-md-6">
                                              <div class="form-group">
                                                  <p class="input-message-icon">
                                                                                                            <input type="text" name="captcha" value="" id="captcha" maxlength="8" placeholder="Enter Captcha Text"  />
                                                      
                                                  </p>
                                                  <div class="help-block with-errors">
                                                      <label class="floating-label" for="inputPassword"></label>
                                                  </div>
                                              </div>
                                        </div>
                                                                                    <div class="col-md-12">
                                            <div class="form-group">
                                                <p class="">
                                                    <input type="checkbox" name="remember" value="1" id="remember" style="margin:0;padding:0"  />
                                                    <span><label for="remember">Remember me</label></span>
                                                </p>                                               
                                            </div>
                                        </div>
                                    </div>

                                    
                                    
                                    <p class="text-center">
                                        <!-- <button type="submit"><i class="icon cf-login"></i> Sign in</button> -->
                                        
                                         <p class="text-center xicon">
                                            <label class="icon cf-login cf-login-btn">    
                                              <!-- <input type="submit" id="btn_cta" class="updated-btn-class sbtn"
                                                   value="Sign In" /> -->
                                                    <input type="submit" name="login" value="Sign In" onclick="return myencryption()" class="updated-btn-class sbtn"  />
                                            </label>
                                        </p>
                                         
                                    </p>
                  
                                    <p class="underline">
                                       <!-- <a href="forgot-password.html">Forgot Password?</a>  -->
                                       <a href="https://connect.csc.gov.in/auth/forgot_password/">Forgot password</a>                                    </p>
                  
                                </form>                                <!-- <div id="msgSubmit" class="h3 text-center hidden"></div> -->
                                <!--
                                      <p>                                          </p> -->
                              

                                      <div id="publickey" style="display:none" value="-----BEGIN PUBLIC KEY-----
MIGfMA0GCSqGSIb3DQEBAQUAA4GNADCBiQKBgQC9BLl8HcSzbdYg5S50RfMznsJf
zzefjAUuYkWS9vViuzs4vw59bbEsIu4bjAlyyTusg8luuXPA9SvO4zYgj1rxe42f
i+tISEuwIcL0f0I+PgmbIBPOhSnTVYmXFmtbZxXgSfLYyzq0WGNZDLJ0s5V1cE6e
EFTb/F6ZCp79sd+/UQIDAQAB
-----END PUBLIC KEY-----"></div>

                            </div>
                        </div>
                    </div>
                </div>
            </div>

            <div class="support-info">
                <ul>
                    <li>
            <a><span><i class="icon cf-envelope"></i></span>care[at]csc[dot]gov[dot]in</li></a>
                    <li>
            <a>
              <span><i class="icon cf-phone"></i></span> 1800 121 3468            </a>
            </li>
                    <li>
            <a href="#">
              <span><i class="icon cf-twitter"></i></span> Digitalseva
            </a>
          </li>
                </ul>
            </div>
        </div>
     <!-- /. left section end -->
     
     
     <!-- right section -->
    
    <!--  logo part and content  -->
        <div class="page-section-content right-side">
      <div class="right-logo">            
        <a href="#" class="logos">
          <img src="https://connect.csc.gov.in/assets/img/digital-india.png" title="Digital India"> 
          <img src="https://connect.csc.gov.in/assets/img/csc.png" title="CSC e-Governance Services">
        </a>
      </div>
            <div class="section-content-table">       
                <div class="section-content-tablecell">
                    <div class="page-section-inner">                        
                        <h4 class="section-title">Welcome to Digital Seva Connect</h4>
                        <div class="section-desc">
                            <p>Gateway to CSC Network!<br>Digital Seva Connect is a secure authentication system for connecting our users to services available on Digital Seva portal.
              Enter your username and password here to authenticate your log-in and enjoy seamless access to Digital Seva portal.</p>
                        </div>
                    </div>
                </div>        
            </div>
      <div class="terms">
        <ul>
          <li><a href="https://digitalseva.csc.gov.in/web/legal" target="blank">Terms & Conditions</a></li> |
          <li><a href="https://digitalseva.csc.gov.in/web/legal" target="blank">Privacy Policy</a></li>
        </ul>         
        <span class="copy-right">Copyright &copy; 2022 CSC e-Governance Services India Limited. All rights reserved.</span>
      </div>      
        </div>
  
    <!-- right section end -->
    </div>
    <!-- /.SINGLE PAGE SECTION END -->
  
<!-- Modal -->
<div id="termsModal" class="modal fade" role="dialog">
  <div class="modal-dialog">

    <!-- Modal content-->
    <div class="modal-content">
      <div class="modal-header">
        <button type="button" class="close" data-dismiss="modal">&times;</button>
        <h4 class="modal-title">Terms & Conditions</h4>
      </div>
      <div class="modal-body">
        <!-- <p>Some text in the modal.</p> -->
      </div>      
    </div>
  </div>
</div>
<!-- Modal -->
<div id="policyModal" class="modal fade" role="dialog">
  <div class="modal-dialog">

    <!-- Modal content-->
    <div class="modal-content">
      <div class="modal-header">
        <button type="button" class="close" data-dismiss="modal">&times;</button>
        <h4 class="modal-title">Privacy Policy</h4>
      </div>
      <div class="modal-body">
        <!-- <p>Some text in the modal.</p> -->
      </div>      
    </div>
  </div>
</div>

<script>
     $(function(){
         var base_url = 'https://connect.csc.gov.in/';
         $('.reload-captcha').click(function(event){
             event.preventDefault();
             $.ajax({
                 url:base_url+'account/regen_create_captcha',
                 success:function(data){
                  //alert(data);
                  $('#captchaimgs').html(data);
                 }
             });            
          });
      });
</script> 
    <!-- JQUERY -->
    <script src="https://connect.csc.gov.in/assets/js/jquery.js"></script>
    <!-- BOOTSTRAP JS -->
    <script src="https://connect.csc.gov.in/assets/js/bootstrap.min.js"></script>
    <!-- VALIDATOR JS -->
    <script src="https://connect.csc.gov.in/assets/js/validator.min.js"></script>
    <!-- FORM SCRIPT -->
    <script src="https://connect.csc.gov.in/assets/js/form-scripts.js"></script>  
    </body>
</html>
