<template>
  <div class="search">
    <h2>Gif Ara</h2>
    <div class="searchGiphy">
      <div class="formItem">
        <label for="">Search</label>
        <input type="text"  @keypress.enter="handleSearch"  name="" v-model="query">
      </div>
      <div class="formSetting">
        <div class="formItem">
          <label for="">Limit</label>
          <input type="text" value="10" v-model="limit" />
        </div>
        <div class="formItem">
          <label for="">Rating</label>
          <select id="rating" class="query-param select-area" v-model="ratings">
            <option value="Y">Y</option>
            <option value="G">G</option>
            <option value="PG">PG</option>
            <option value="PG-13">PG-13</option>
            <option value="R">R</option>
          </select>
        </div>
        <div class="formItem">
          <label for="">Language</label>
          <select id="lang" class="query-param select-area" v-model="language">
          	<option value="en">en</option>
          	<option value="es">es</option>
          	<option value="pt">pt</option>
          	<option value="id">id</option>
          	<option value="fr">fr</option>
          	<option value="ar">ar</option>
          	<option value="tr">tr</option>
          	<option value="th">th</option>
          	<option value="vi">vi</option>
          	<option value="de">de</option>
          	<option value="it">it</option>
          	<option value="ja">ja</option>
          	<option value="zh-CN">zh-CN</option>
          	<option value="zh-TW">zh-TW</option>
          	<option value="ru">ru</option>
          	<option value="ko">ko</option>
          	<option value="pl">pl</option>
          	<option value="nl">nl</option>
          	<option value="ro">ro</option>
          	<option value="hu">hu</option>
          	<option value="sv">sv</option>
          	<option value="cs">cs</option>
          	<option value="hi">hi</option>
          	<option value="bn">bn</option>
          	<option value="da">da</option>
          	<option value="fa">fa</option>
          	<option value="tl">tl</option>
          	<option value="fi">fi</option>
          	<option value="iw">iw</option>
          	<option value="ms">ms</option>
          	<option value="no">no</option>
          	<option value="uk">uk</option>
          </select>
        </div>
        <div class="saver hiddenText">&nbsp;</div>
      </div>
    </div>
    <button type="button" name="button" class="btnSend" @click="handleSearch">Search</button>
  </div>
</template>


<script>
  export default{
    data(){
      return{
        query: '',
        limit: '12',
        ratings: 'G',
        language: 'en' 
      }
    },
    methods: {
      handleSearch(){
        this.$emit('SearchRequested', this.query, this.limit, this.ratings, this.language)
      }
    }
  }
</script>
