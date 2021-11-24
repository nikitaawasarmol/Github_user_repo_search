<template functional>
  <header>
    <div class="space">
    <h3>Name</h3>
     <span>{{props.profile.name || "'NAME'"}}</span>
    </div>
    <div class="space">
    <h3>Bio</h3>
    <span>{{props.profile.bio || "'BIO'"}}</span>
    </div>
  </header>
</template>

<style scoped>
header {
  display: flex;
  flex-direction: row;
  justify-content: start;
  align-items: flex-start;
  background: #fff;
  flex-wrap: wrap;
  width: 100%;
  margin-top: 20px;
}
.space {
  border: 1px solid gray;
  display: flex;
  padding: 20px;
  border-radius: 9px;
  flex-direction: column;
  justify-content: start;
  align-items: center;
  background: #fff;
  flex-wrap: wrap;
  width: 100%;
  margin-top: 20px;

}
hr {
  width: 100%;
  margin-bottom: 10px;
}
h3 {
  margin: 5px 0 0 0 ;
  color: #0969da;

}
span {
  font-weight: 800;
  font-family: 'Shippori Antique', sans-serif;
  font-size: 16px;
  text-align: center;
  margin-top: 5px;

}
.link {
  text-decoration: none;
  color: #000;
  font-weight: 500;
  font-family: "Courier New", Courier, monospace;
  font-size: 16px;
  text-align: center;
}
.link:hover {
  color: blue;
}
</style>