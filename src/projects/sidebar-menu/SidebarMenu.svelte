<script>
    // let navWidth = 0;
    let navOpen = false;

    const handleMenu = () => {
        navOpen = !navOpen;
        // navOpen ? navWidth = 50 : navWidth = 0;
    }

    const openMenuByKey = (e) => {
        console.log(e.code);
        if (e.code === 'IntlBackslash') {
            navOpen = !navOpen;
        }
    }
</script>

<!-- MarkUp -->
<svelte:window on:keydown={openMenuByKey}/>

<h2>Sidebar Menu</h2>
<p>You can also toggle the opening of the sidebar menu by pressing the "\" (IntlBackslash) key on the keyboard!</p>

<div id="mySidenav" class="sidenav" class:openMenu={navOpen}>
    <a href="#closer" class="closebtn" on:click={handleMenu}>&times;</a>
    <a href="#a">About</a>
    <a href="#s">Services</a>
    <a href="#c">Clients</a>
    <a href="#d">Contact</a>
</div>
  
<!-- Use any element to open the sidenav -->
<span on:click={handleMenu}>
    {#if !navOpen} 
        <img src="https://s2.svgbox.net/hero-solid.svg?ic=menu&color=000" alt="Menu Icon">
    {:else}
        <img src="https://s2.svgbox.net/hero-solid.svg?ic=x&color=000" alt="Close Icon">
    {/if}
</span>

<style>
    span {
        position: absolute;
        right: 5%;
        margin-top: 5%;
        width: 40px;
        height: auto;
        cursor: pointer;
    }
/* The side navigation menu */
.sidenav {
  height: 100%; /* 100% Full-height */
  /* 0 width - change this with JavaScript */
  width: 0; 
  position: fixed; /* Stay in place */
  z-index: 1; /* Stay on top */
  top: 0;
  left: 0;
  background-color: #111; /* Black*/
  overflow-x: hidden; /* Disable horizontal scroll */
  padding-top: 60px; /* Place content 60px from the top */
  transition: 0.5s; /* 0.5 second transition effect to slide in the sidenav */
}

/* The navigation menu links */
.sidenav a {
  padding: 8px 8px 8px 32px;
  text-decoration: none;
  font-size: 25px;
  color: #818181;
  display: block;
  transition: 0.3s;
}

/* When you mouse over the navigation links, change their color */
.sidenav a:hover {
  color: #f1f1f1;
}

/* Position and style the close button (top right corner) */
.sidenav .closebtn {
  position: absolute;
  top: 0;
  right: 25px;
  font-size: 36px;
  margin-left: 50px;
}

.openMenu {
    width: 50%;
}

/* Style page content - use this if you want to push the page content to the right when you open the side navigation */
#main {
  transition: margin-left .5s;
  padding: 20px;
}

/* On smaller screens, where height is less than 450px, change the style of the sidenav (less padding and a smaller font size) */
@media screen and (max-height: 450px) {
  .sidenav {padding-top: 15px;}
  .sidenav a {font-size: 18px;}
}
</style>