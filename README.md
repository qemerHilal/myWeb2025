<!DOCTYPE html>
<html>
    <head>
      
      <h3>This project shows you, how to show what you want and hide the rest!</h3>
      
      <title> creating a data filter </title>
        <style>
       
        ul{

           list-style: none;
           margin:0 0 30px;
           padding:0;
            display:flex;
             justify-content: center;
             padding:15px;
             transition:0.3s;
             
        }
        ul li{


             border-radius: 25px;
            cursor: pointer;
            padding:10px 20px;
            background-color: white;
          

        }

        ul li.active{
            background-color: blue;
            color:white;
        }

        .hidden{
           display: none;
        }

        .items{

            display:grid;
            grid-template-columns: repeat(auto-fill, minmax(250px,1fr));
            max-width:1100px;
            gap:20px;
            margin:auto;
        }
        .item{
            position:relative;
            overflow:hidden;
            box-shadow:0 4px 10px rgb(0, 0, 0,0,0.1);
            border-radius:15px;
            transition:transform 0.3s;


        }
        .item:hover{
         transform:scale(1.03);
        }
        .item img,video{
            
           
            width:100%;
            height:200px;
            object-fit:cover;
            display:block;
          
  
        }
        .item span{
            position:absolute;
            bottom:10px;
            left:10px;
            border-radius:8px;
            color:white;
            background: rgba(10, 10, 10, 0.6);
            font-size:14px;
            padding:5px 10px;
        }


        </style>
    </head>

<body>
    <ul>
        <li class="active" data-filter="*">All</li>
        <li data-filter="photos">Photos</li>
        <li data-filter="videos">Videos</li>
        <li data-filter="articles">Articles</li>

    </ul>

<div class="items">

     <div class="item photos">
        <img src="picMotivation1.jpg">
        <span>photo 1</span>
    </div>
    <div class="item photos">
        <img src="picMotivation2.jpg">
        <span>photo 2</span>
    </div>
    <div class="item videos">
        <video controls>
            <source src="motivation1.mp4" type="video/mp4">
            <span>video 1</span>
        </video>
        
        
    </div>
    <div class="item videos">
        <video controls>
            <source src="motivation2.mp4" type="video/mp4">
            <span>video 2</span>
        </video>
    </div>

    <div class="item articles">
        <img src="How to Become Self-Motivated.jpg">
        <span>article 1</span>
    </div>
    
     <div class="item articles">
        <img src="motivation.png">
        <span>article 2</span>
    </div>

   

</div>
   <script>
     
     const filters=document.querySelectorAll("ul li");
     const items=document.querySelectorAll(".item");
     
     filters.forEach(filter=>{filter.addEventListener("click",()=>{
         console.log("yes i was invoked");
        filters.forEach(btn=>{btn.classList.remove("active")});

        filter.classList.add("active");
        const filterValue=filter.getAttribute("data-filter");
        items.forEach(item=>{
            if(filterValue==='*' || item.classList.contains(filterValue) )
            {
               item.classList.remove("hidden");

            }
            else{
                item.classList.add("hidden");
            }
        })

        

     })})

   </script>
</body>

</html>
