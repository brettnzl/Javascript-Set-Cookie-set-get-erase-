# Javascript-Set-Cookie-set-get-erase-
// Function to set a cookie. 
function setCookie(cname, cvalue, exdays) {
    const d = new Date();
    d.setTime(d.getTime() + (exdays*24*60*60*1000));
    let expires = "expires="+ d.toUTCString();
    document.cookie = cname + "=" + cvalue + ";" + expires + ";path=/";
}

// Function to get a cookie
function getCookie(cname) {
    let name = cname + "=";
    let decodedCookie = decodeURIComponent(document.cookie);
    let ca = decodedCookie.split(';');
    for(let i = 0; i <ca.length; i++) {
      let c = ca[i];
      while (c.charAt(0) == ' ') {
        c = c.substring(1);
      }
      if (c.indexOf(name) == 0) {
        return c.substring(name.length, c.length);
      }
    }
    return "";
}

function eraseCookie(name) {   
    document.cookie = name+'=; Max-Age=-99999999;';  
}

Add the following code then create a toggle or a change to use it. 

 // Toggle Button for Dark Mode
    $('.nighttoggle .toggle-switch').on('change', function(){
        if (this.checked) {
            $('html').addClass('darkmode');
            setCookie('darkmode', true, 1);
        } else {
            $('html').removeClass('darkmode');
            eraseCookie('darkmode');
        }
    });
