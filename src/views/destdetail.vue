<template>
<div class="page">
  <section>
    <section>
    <div class="p-5"></div>
    </section>

  <nav aria-label="breadcrumb" class="container">
  <ol class="breadcrumb">
    <li class="breadcrumb-item"><router-link to="/">{{$translate(['Beranda','Home'])}}</router-link></li>
    <li class="breadcrumb-item"><router-link to="/Destination">{{$translate(['Destinasi','Destination'])}}</router-link></li>
    <li class="breadcrumb-item active" aria-current="page">{{this.nama}}</li>
  </ol>
</nav>

  <section v-if="errored">
    <p>Mohon maaf, terjadi kesalahan saat mengambil data. Silakan coba beberapa saat lagi.</p>
  </section>

  <section v-else>
    
    <!-- Whole Card -->
    <div class="container">
          <div class="row">
            <div id="slideshow" class="carousel d-lg-block slide" data-ride="carousel">
              <ol class="carousel-indicators">
                <li data-target="#slideshow" data-slide-to="0" class="active"></li>
                <li data-target="#slideshow" data-slide-to="1"></li>
                <li data-target="#slideshow" data-slide-to="2"></li>
                <li data-target="#slideshow" data-slide-to="3"></li>
                <li data-target="#slideshow" data-slide-to="4"></li>
              </ol>
              <div class="carousel-inner">
                <div class="carousel-item carousel-member-item active">
                  <img id="img1-desktop" class="memberpage img-fluid d-block" alt="Image 1">
                </div>
                <div class="carousel-item carousel-member-item">
                  <img id="img2-desktop" class="memberpage img-fluid d-block" alt="Image 2">
                </div>
                <div class="carousel-item carousel-member-item">
                  <img id="img3-desktop" class="memberpage img-fluid d-block" alt="Image 3">
                </div>
                <div class="carousel-item carousel-member-item">
                  <img id="img4-desktop" class="memberpage img-fluid d-block" alt="Image 4">
                </div>
                <div class="carousel-item carousel-member-item">
                  <img id="img5-desktop" class="memberpage img-fluid d-block" alt="Image 5">
                </div>
                <a class="carousel-control-prev" href="#slideshow" role="button" data-slide="prev">
                  <span class="carousel-control-prev-icon" aria-hidden="true"></span>
                  <span class="sr-only">Previous</span>
                </a>
                <a class="carousel-control-next" href="#slideshow" role="button" data-slide="next">
                  <span class="carousel-control-next-icon" aria-hidden="true"></span>
                  <span class="sr-only">Next</span>
                </a>
              </div>
            </div>

            <div class="d-none d-lg-block col">
              <!-- Card on desktop-->
              <div class="card my-3">
                <div class="card-body">
                <div class="row align-center">
                  <div class="col-2 my-auto"><i class="bi bi-geo-alt-fill"></i></div>
                  <div class="col my-auto"><div v-if="loading">Loading...</div><a v-bind:href="`https://www.google.com/maps/search/?api=1&query=${this.lat},${this.long}`" class="text-black" target="_blank">{{this.alamat}}</a></div>
                </div></div>
              </div>
              <div class="card my-3">
                <div class="card-body">
                  <div class="row align-center">
                  <div class="col-2 my-auto"><i class="bi bi-envelope-fill"></i></div>
                  <div class="col my-auto"><div v-if="loading">Loading...</div><a v-bind:href="`mailto:${this.email}`" class="text-black">{{this.email}}</a></div>
                  </div>
                </div>
              </div>
              <div class="card my-3">
                <div class="card-body">
                  <div class="row align-center">
                  <div class="col-2 my-auto"><i class="bi bi-whatsapp"></i></div>
                  <div class="col my-auto"><div v-if="loading">Loading...</div><a v-bind:href="`https://wa.me/+${ this.whatsapp }`" class="text-black">{{this.whatsapp}}</a></div>
                  
                  </div>
                </div>
              </div>
              <div class="card my-3">
                <div class="card-body">
                  <div class="row align-center">
                  <div class="col-2 my-auto"><i class="bi bi-bookmarks-fill"></i></div>
                  <div class="col my-auto"><div v-if="loading">Loading...</div>{{this.kategori}}</div></div>
                </div>
              </div>
            </div>
          </div>
        <!-- Card in smaller screen -->
        <div class="d-block d-lg-none container">
          <div class="card my-3">
            <div class="card-body">
              <div class="row align-center">
                  <div class="col-1 mr-3"><i class="bi bi-geo-alt-fill"></i></div>
                  <div class="col-9 my-auto"><div v-if="loading">Loading...</div>{{this.alamat}}</div>
                </div></div>
          </div>
          <div class="card my-3">
            <div class="card-body">
              <div class="row align-center">
                  <div class="col-1 mr-3"><i class="bi bi-envelope-fill"></i></div>
                  <div class="col-auto my-auto"><div v-if="loading">Loading...</div>{{this.email}}</div></div>
            </div>
          </div>
          <div class="card my-3">
            <div class="card-body">
              <div class="row align-center">
              <div class="col-1 mr-3"><i class="bi bi-whatsappl"></i></div>
              <div class="col-auto my-auto"><div v-if="loading">Loading...</div><a v-bind:href="`https://wa.me/+${ this.whatsapp }`" class="text-black">{{this.whatsapp}}</a></div></div>
            </div>
          </div>
          <div class="card my-3">
                <div class="card-body">
                  <div class="row align-center">
                  <div class="col-1 mr-3"><i class="bi bi-bookmarks-fill"></i></div>
                  <div class="col-auto my-auto"><div v-if="loading">Loading...</div>{{this.kategori}}</div></div>
                </div>
          </div>
        </div>
      </div>

  </section>
<section class="p-4">
        <div class="text-justify px-5">
        <h3 class="text-center">{{$translate(['About','Tentang'])}} {{this.nama}}</h3>
        <hr>
        <div v-if="loading">Loading...</div><p>{{this.deskripsi}}</p>
        </div>
</section>
  </section>
</div>
</template>

<script>
import axios from "axios";

export default {
  data: () => ({
    lat: null,
    long: null,
    nama: null,
    alamat: null,
    email: null,
    whatsapp: null,
    deskripsi: null,
    img: null,
    kategori: null,
    loading: true,
    errored: false
  }),
  /*watch: {
$route(to, from){
console.log();

  },*/
    created(){
      var arrayke = this.$route.params.id.toString()
      console.log(arrayke);
      let baseUrl =
      "https://oobad.id/api/";
      axios.get(baseUrl + 'offices.php?page=1&lat=-8.6649188&long=115.2384802')
      .then((response) => {
        this.lat = response.data.data.items[arrayke].lat;
        this.long = response.data.data.items[arrayke].long;
        var koordinat = this.lat+', '+this.long;
        this.nama = response.data.data.items[arrayke].name;
        this.img1 = response.data.data.items[arrayke].images[0];
        this.img2 = response.data.data.items[arrayke].images[1];
        this.img3 = response.data.data.items[arrayke].images[2];
        this.img4 = response.data.data.items[arrayke].images[3];
        this.img5 = response.data.data.items[arrayke].images[4];
        this.email = 'info@bamboomedia.net';
        this.deskripsi = response.data.data.items[arrayke].description;
        this.alamat = response.data.data.items[arrayke].address;
        this.whatsapp = response.data.data.items[arrayke].whatsapp;
        this.kategori = response.data.data.items[arrayke].type.name;
        console.log(koordinat)
        console.log(this.kategori);
        console.log(this.name);
        console.log(this.whatsapp);
        console.log(this.alamat);
        console.log(this.img);
        console.log(this.deskripsi);
        document.title = this.nama + " - Oobad";
        document.getElementById("img1-desktop").src = this.img1;
        document.getElementById("img2-desktop").src = this.img2;
        document.getElementById("img3-desktop").src = this.img3;
        document.getElementById("img4-desktop").src = this.img4;
        document.getElementById("img5-desktop").src = this.img5;
      })
      .catch(error => {
        console.log(error)
        this.errored = true
      })
      .finally(() => this.loading = false)
    }
  }

  if ($(".Page").height()<$(window).height()){
        $(".footer_wrapper").addClass("fixed");
    }else{
        $(".footer_wrapper").removeClass("fixed");
    }
</script>

<style>
.rs-header-img {
  width: 60%;
  height: 60%;
}

.carousel-member {
  width:unset;
  height:unset;
}

.carousel-member-item img {
  position:relative;
}

.memberpage{
  max-width: 560px;
  max-height: 490px;
}

</style>