<template>
<div class="container">
  <h1>BIODATA ALAMAT TINGGAL</h1>
  <div class="dropdown">
    <span>Provinsi:</span>
    <select v-model="pilih_provinsi">
      <option value="">Pilih Provinsi</option>
      <option v-for="(index, province) in data_lokasi" :value="province" :key="index">{{province}}</option>
      </select>
      </div>
      <div class="drop-item">
        <span>Kota:</span>
        <select :disabled="kota.length == 0" v-model="pilih_kota">
           <option value="">Pilih Kota</option>
           <option v-for="(index, kota) in kota" :value="kota" :key="index">{{kota}}</option>
           </select>
           </div>
           <div class="drop-item">
             <span>Kecamatan:</span>
             <select :disabled="kecamatan.length == 0" v-model="pilih_kecamatan">
               <option value="">Pilih Kecamatan</option>
               <option v-for="kec in kecamatan" :value="kec" :key="kec">{{kec}}</option>
               </select>
               </div>
               <div class="hasil">
                 <p v-if="pilih_provinsi&&pilih_kota&&pilih_kecamatan">
                  Kamu Tinggal Di Kecamatan {{pilih_kecamatan}}, Kota {{pilih_kota}}, Provinsi {{pilih_provinsi}}</p>
                   </div>
                   </div>
                   </template>

<script>
export default {
  data: () => ({
    kota: [],
    kecamatan: [],
    pilih_provinsi: '',
    pilih_kota: '',
    pilih_kecamatan: '',
    data_lokasi: {
      'DKI Jakarta ': {
        'Jakarta Barat ': ['Cengkareng', 'Grogol Petamburan', 'Taman Sari', 'Tambora', 'Kebon Jeruk', 'Kalideres', 'Palmerah', 'Kembangan'],
        'Jakarta Timur ': ['Cakung', 'Cipayung', 'Ciracas', 'Duren Sawit', 'Jatinegara', 'Kramat Jati', 'Makasar', 'Matraman', 'Pasar Rebo', 'Pulo Gadung'],
        'Jakarta Selatan ': ['Cilandak', 'Jagakarsa', 'Kebayoran Baru', 'Kebayoran Lama', 'Mampang Prapatan', 'Pancoran', 'Pasar Minggu', 'Pesanggrahan', 'Setiabudi', 'Tebet'],
        'Jakarta Utara ': ['Cilincing', 'Kelapa Gading', 'Koja', 'Pademangan', 'Penjaringan', 'Tanjung Priok'],
        'Jakarta Pusat ': ['Cempaka Putih', 'Johar Baru', 'Kemayoran', 'Menteng', 'Sawah Besar', 'Senen', 'Tanah Abang'],
        'Kepulauan Seribu ': ['Kepulauan Seribu Selatan', 'Kepulauan Seribu Utara']
      },
      'DIY Yogyakarta ': {
        'Bantul ': ['Bambanglipuro', 'Banguntapan', 'Bantul', 'Dlingo', 'Imogiri', 'Jetis', 'Kasihan', 'Kretek', 'Pajangan', 'Pandak', 'Piyungan', 'Pleret', 'Pundong', 'Sanden', 'Sedayu', 'Sewon', 'Srandakan'],
        'Gunungkidul ': ['Gedangsari', 'Girisubo', 'Karangmojo', 'Ngawen', 'Nglipar', 'Paliyan', 'Panggang', 'Playen', 'Ponjong', 'Purwosari', 'Rongkop', 'Saptopsari', 'Semanu', 'Semin', 'Tanjungsari', 'Tepus', 'Wonosari'],
        'Sleman ': ['Berbah', 'Cangkringan', 'Depok', 'Gamping', 'Godean', 'Kalasan', 'Minggir', 'Mlati', 'Moyudan', 'Ngaglik', 'Ngemplak', 'Pakem', 'Prambanan', 'Seyegan', 'Sleman', 'Tempel', 'Turi'],
        'Kulon Progo ': ['Galur', 'Girimulyo', 'Kalibawang', 'Kokap', 'Lendah', 'Nanggulan', 'Panjatan', 'Pengasih', 'Samigaluh', 'Sentolo', 'Temon', 'Wates'],
        'Yogyakarta ': ['Mantrijeron', 'Kraton', 'Mergangsan', 'Umbulharjo', 'Kotagede', 'Gondokusuman', 'Danurejan', 'Pakualaman', 'Gondomanan', 'Ngampilan', 'Wirobrajan', 'Gedongtengen', 'Jetis', 'Tegalrejo']
      }
    }
  }),
  watch: {
    pilih_provinsi () {
      this.kota = []
      this.kecamatan = []
      this.pilih_kota = ''
      this.pilih_kecamatan = ''
      // Populate list of countries in the second dropdown
      if (this.pilih_provinsi.length > 0) {
        this.kota = this.data_lokasi[this.pilih_provinsi]
      }
    },
    pilih_kota () {
      this.kecamatan = []
      this.pilih_kecamatan = ''
      if (this.pilih_kota.length > 0) {
        this.kecamatan = this.data_lokasi[this.pilih_provinsi][this.pilih_kota]
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.container {

  max-width: 700px;

  margin: 0 auto;

}

.dropdown {

  padding: 20px;

  width: 700px;

  margin-bottom: 10px;

  box-shadow: 0 4px 8px 0 rgba(0,0,0,0.2);

  border-radius: 5px;

  text-align: center;

  background-color: pink;

}

.hasil {

  width: 700px;
  padding: 20px;

  box-shadow: 0 4px 8px 0 #7c7c78;

  border-radius: 5px;

  text-align: center;

}

.drop-item {

  padding: 20px;

  width: 700px;

  margin-bottom: 10px;

  box-shadow: 0 4px 8px 0 rgba(0,0,0,0.2);

  border-radius: 5px;

  text-align: center;

  background-color: pink;
}

h1 {

  color: #808080f8;

  font-family: 'Rainwood';

}

@font-face {
  font-family: 'Rainwood';
  src: url('/Rainwood.otf') format(otf);
}
</style>
