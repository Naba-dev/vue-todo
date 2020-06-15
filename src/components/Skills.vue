<template>
    <div class="hello">
        <div class="holder">
           <form action="">
                <input type="text" placeholder="Enter a Skill" v-model="skill" v-validate="'min:5'" name="skill" class="form-control">
                <span v-if="errors.has('skill')"> {{ errors.first('skill') }} </span>
                <button v-on:click.prevent = "insertSkill" class="btn btn-info mt-3 mb-2"> Add </button>
                </form>
            <ul>
                
                <li v-for="(s,i) in skills" :key="s">
                    {{s}}   
                <span class="remove" v-on:click="removeItems(i)"> Delete </span>
                </li>
            </ul>
        </div>
    </div>
</template>

<script>
export default {
    name: "skills",
    data() {
        return {
            skill: '',
            skills: [
            ]
        }
    },
    methods: {
        insertSkill() {
               this.$validator.validateAll().then((result) => {
                   if(result) {
                        this.skills.push(this.skill);
                        this.skill = ''; 
                   }
                   else{
                       console.log("Not Valid")
                   }
                })             
        },

        removeItems(i) {
        // this.todos.splice(i,1); //Delete using JS method
        this.$delete(this.skills,i); //Delete using Vue method
        },         
    }
}
</script>

<style scoped>
.hello {
    position: absolute;
    top: 30vh;
    left: 20vw;
    width: 60vw;
}
 .holder {
    background: #fff;
    padding: 30px;
  }

  .holder ul {
    margin: 0;
    padding: 0;
    list-style-type: none;
  }
  
  .holder ul li {
    padding: 10px;
    font-size: 1.3em;
    background-color: #E0EDF4;
    border-left: 5px solid #3EB3F6;
    margin-bottom: 2px;
    color: #3E5252;
  }

  p {
    text-align:center;
    padding: 30px 0;
    color: gray;
  }

  .container {
    box-shadow: 0px 0px 40px lightgray;
  }
  .remove:hover {
  cursor:pointer;
  }

  .remove {
  color: red;
  font-size: .8em;
  float:inline-end;
  margin-top: 4px;

  }
.btn {
    display: block;
    width: 100px;
}
span {
    color: red;
}

</style>