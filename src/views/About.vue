<template>
<div class="Page">
  <nav class="container pt-5 mt-5">
    <ol class="breadcrumb" >
      <li class="breadcrumb-item"><router-link to="/">{{ $translate(["Beranda", "Home"]) }}</router-link></li>
      <li class="breadcrumb-item active" aria-current="page">
        {{ $translate(["Tentang", "About"]) }}
      </li>
    </ol>

    <section class="p-4">
      <div class="text-justify px-5">
        
    <h2 class="font-weight-bold text-center pb-3">
      {{ $translate(["Tentang", "About"]) }}
    </h2>
        <hr />
        <p>
          {{ $translate(["Yang terpenting dalam hidup adalah waktu. Bisa panjang umur dalam kondisi sehat adalah impian semua orang. Karena sehat adalah satu-satunya syarat untuk bersyukur dan pada akhirnya bahagia. Mari berlibur bersama keluarga sambil merawat kesehatan fisik, mental dan spiritual.", "The most important thing in life is time. Being able to live a long life in a healthy condition is everyone's dream. Because being healthy is the only condition for being grateful and ultimately happy. Let's take a vacation with family while taking care of our physical, mental and spiritual health."]) }}
        </p>
        <br>
        <p class="pb-5 mb-5">
          {{ $translate(["Oobad adalah pusat informasi dan reservasi wisata kesehatan di Pulau Dewata, Bali. Dengan berkembangnya SEZ Kesehatan di Sanur Bali, memicu tumbuhnya industri yang berkaitan dengan kesehatan, baik medis maupun wellness. Temukan talenta terbaik untuk kesehatan Anda, investasikan pada aset terpenting dalam hidup kita, yaitu: SEHAT dan DAMAI", "Oobad is a health tourism information and reservation center on the Island of the Gods, Bali. With the development of the Health SEZ in Sanur Bali, triggering the growth of industries related to health care, both medical and wellness. Find the best talent for your health, invest in the most important asset in our life, namely: HEALTHY and PEACEFUL"]) }}

        </p>
      </div>
    </section>
    <br />
  </nav>
</div>
</template>


<script>
export default {
  data() {
    return {
      images: {
        cover1: require("@/assets/hero/flat.png"),
        cover2: require("@/assets/gallery/section_bg01.png"),
        about: require("@/assets/gallery/pexels-tom-fisk-1692693.jpg"),
        logo: require("@/assets/logo/logo.png"),
      },
    };
  },
};
</script>

<style>
.container {
  position: relative;
}

.container-fluid {
  overflow: hidden;
  position: relative;
  text-align: left;
  width: 100%;
}

#footer { 
  position:absolute; 
  width:100%; 
  height:150px; 
  color: black;
  background-color: #6ec3ff;
  padding-block: 2em;
  }

.img-about {
  max-width: 100%;
  max-height: 100%;
}

.centered {
  position: absolute;
  top: 42%;
  left: 50%;
  transform: translate(-50%, -50%);
}

.t-color {
  color: #6ec3ff;
}
</style>