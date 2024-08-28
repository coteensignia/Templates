
<script>
export default {
  name: 'FormInterfaz',
  data() {
    return {
      colorFondo: '',
      colorTexto: '',
      mostrar: '',
      borde: '',
      contenido: '',
      opaco: '',
      tipoLetraSelected: '',
      tipoLetra: ['monospace', 'serif', 'sans-serif'],
      tamanoLetraSelected: '',
      tamanoLetra: [
        { value: '10px', label: 'Pequeño' },
        { value: '30px', label: 'Mediano' },
        { value: '50px', label: 'Grande' }
      ]
    }
  }
}
</script>
<template>

  <div class="container">
    <!-- Bloque Izquierda -->
    <form class="form">
      <!-- Color Fondo -->
      
        <label for="fondo">Color de fondo</label>
        <input type="color" id="fondo" v-model="colorFondo" class="form-control" />
      
      <!-- Color Texto -->
      
        <label for="colorTexto">Color de texto</label>
        <input type="color" id="colorTexto" v-model="colorTexto" class="form-control" />
      
      <!-- Mostrar Texto -->
      <div class="form-group">
        <label for="mostrarTexto">Mostrar texto</label>
        <input type="checkbox" id="mostrarTexto" v-model="mostrar" />
      </div>
      <!-- Borde -->
      
        <label for="borde">Borde</label>
        <input type="range" name="borde" id="borde" v-model="borde" />
        
     
       
      
      <!-- Contenido -->
      
        <label for="contenido">Contenido</label>
        <textarea id="contenido" v-model="contenido"></textarea>
      
      <!-- Tipografía -->
      
        <label for="tipografia">Tipografía</label>
        <select name="tipo" id="tipografia" v-model="tipoLetraSelected">
          <option v-for="tipografia in tipoLetra" :key="tipografia" :value="tipografia">
            {{ tipografia }}
          </option>
        </select>
    
      <!-- opaco -->
      <div class="form-group" >
        <label for="opaco">Opaco</label>
        <input type="checkbox" id="opaco" v-model="opaco" />
      </div>
      <!-- Tamaño Letra -->
      
        <label for="tamañoLetra">Tamaño Letra</label>
        <div class="form-group ">
        <div class="check-item " v-for="tamano in tamanoLetra" :key="tamano.value">
          <div class="form-group ">
           <input
            type="radio"
            :name="tamano.value"
            :value="tamano.value"
            :id="tamano.value"
            v-model="tamanoLetraSelected"
          />
          <label :for="tamano.value">{{ tamano.label }}</label>
          </div>
         
        </div>
      </div>
    </form>
    <!-- Bloque Derecha -->
    <div
      id="resultado"
      :style="{
        backgroundColor: colorFondo,
        color: colorTexto,
        borderRadius: `${borde}%`,
        fontFamily: tipoLetraSelected,
        fontSize: tamanoLetraSelected
      }"
      :class="{
        opaco: opaco
      }"
    >
      <p v-show="mostrar">
        {{ contenido }}
      </p>
    </div>
  </div>
</template>

<style scoped>
.container {
  display: flex;
  align-items: center;
  gap: 2rem;
}

.flex-row {
  display: flex;
  gap: 10px;
}

.flex-column {
  display: flex;
  flex-direction: column;
}

form {
  display: flex;
  flex-direction: column;
  background-color: #2f4f4f;
  width: 500px;
  padding-inline: 2.5rem;
  padding-block: 2rem;
  color: white;
  font-size: 20px;
  font-family:sans-serif;

}


input, textarea, label {
  width: 100%;
  margin-bottom: 10px;
  margin-top: 10px;
  resize: none;
}


.form-group {
 display: flex;
 

 
 input{
height: 20px;
 }

}

#mostrarTexto, #opaco{
  position: relative;
  left: -150px; 
 
  
  }

#resultado {
  height: 450px;
  width: 450px;
  display: grid;
  place-content: center;
}

.opaco {
  opacity: 0.5;
}
</style>
