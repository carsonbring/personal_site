<script>
    import { Navbar, Footer } from '$lib';
 
</script>

<body class="flex flex-col min-h-screen bg-gradient-to-r from-emerald-950   to-slate-900">
    <Navbar/>
    <!-- Main Heading -->
<br>
<div class="container mx-auto my-8 p-4">
    <div class="bg-pale shadow-lg rounded-lg p-2 opacity-90">
        <div class="bg-slate-950 shadow-lg rounded-lg p-8">
            <h1 class="text-center text-orange-100">Welcome to Carson Bring's Personal Website</h1>
            <br>
            <!-- Subheading -->
            <h2 class="text-center text-pale">
            Hello and welcome! This website serves as a place for me to
            host my blog, information about myself, and future projects
            that I will host using the same backend I use to host my blog.
            <br> <br>
            The code that I used to make my backend and front-end are hosted
            in their own respective repos on my github. 

            </h2>

            
        </div>
    </div>
    <br>
    <br>
    <div class="flex flex-col md:flex-row justify-between container mx-auto my-8 p-4">
        <!-- Left Divstyle="align-self: flex-start" -->
        <div class="bg-pale shadow-lg rounded-lg p-2 opacity-90 mb-4 md:mb-0 md:mr-2 w-full md:w-8/12" style="align-self: flex-start">
            <div class="bg-slate-950 shadow-lg rounded-lg p-8 ">
                <h1 class="text-center text-orange-100">About Me</h1>
                <br>
                
                <ul class="text-pale list-disc ml-5">
                    <li>Senior in NDSU's Computer Science program</li>
                    <br>
                    <li>Graduating in Fall 2024</li>
                    <br>
                    <li>Current treasurer of the NDSU Chapter of the Association for Computing Machinery</li>
                    <br>
                    <li>NDSU Engineering Ambassador</li>
                    <br>
                    <li>Worked the last two summers at Be The Match on their Salesforce team</li>

                </ul>
                <br>
                <hr>
                <br>

                <h1 class="text-center text-orange-100">My Interests</h1>
                <br>
                
                <ul class="text-pale list-disc ml-5">
                    <li>Painting</li>
                    <br>
                    <li>Lifting</li>
                    <br>
                    <li>Messing around with linux and my home server</li>
                    <br>
                    <li>Playing the occasional video game</li>
                    <br>
                    <li>Investing in the Stock Market</li>
                    <br>
                    <li>Anime</li>

                </ul> 
                <br>
                <h2 class="text-pale"><i>I am usually in the ACM room so come talk to me!</i> </h2>
            </div>
        </div>
    
        <!-- Right Div -->
        <div class="bg-pale shadow-lg rounded-lg p-2 opacity-90 w-full md:w-5/12" style="align-self: flex-start">
            <div class="bg-slate-950 shadow-lg rounded-lg p-8">
                <h2 class="text-center text-pale">Some of my paintings</h2>
                <br>
                <img src="https://imgur.com/afXDQko.jpg"  alt="Clown Fish"/>
                <br>
                <img src="https://imgur.com/14U5kim.jpg"  alt="Flowers"/>
                <br>
                <img src="https://imgur.com/a4aYHIo.jpg"  alt="Betta Fish"/>
                <br>
            </div>
        </div>
    </div>
</div>



   
</body>

<Footer />