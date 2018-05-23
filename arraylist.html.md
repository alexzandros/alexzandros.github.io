<!DOCTYPE html>
<html>

<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>arraylist.html</title>
  <link rel="stylesheet" href="https://stackedit.io/style.css" />
</head>

<body class="stackedit">
  <div class="stackedit__html"><h1 id="arraylist-y-linkedlist-en-java-¿son-iguales">ArrayList y LinkedList en Java, ¿son iguales?</h1>
<p>Si revisamos el paquete java.util podremos observar que entre las muchas clases que se encuentran definidas en él están dos implementaciones diferentes de la Interfaz <code>List</code>, a saber <code>ArrayList</code> y <code>LinkedList</code>, podemos pensar que es un desperdicio de recursos tener dos clase diferentes para implementar una lista, pero no es así, vamos a dar primera aproximación a las diferencias existentes entre ambas implementaciones.</p>
<p><strong>ArrayList.</strong>  Internamente maneja un arreglo para almacenar los elementos, lo que hace que sus operaciones de asignación, recuperación y búsqueda sean muy rápidas, con una complejidad de O(1), que quiere decir que se hacen en tiempo constante independientemente de la longitud del arreglo.</p>
<pre class=" language-java"><code class="prism  language-java"><span class="token keyword">import</span> java<span class="token punctuation">.</span>util<span class="token punctuation">.</span>*<span class="token punctuation">;</span>

<span class="token keyword">public</span> <span class="token keyword">class</span> <span class="token class-name">HelloWorld</span><span class="token punctuation">{</span>

     <span class="token keyword">public</span> <span class="token keyword">static</span> <span class="token keyword">void</span> <span class="token function">main</span><span class="token punctuation">(</span>String <span class="token punctuation">[</span><span class="token punctuation">]</span>args<span class="token punctuation">)</span><span class="token punctuation">{</span>
        <span class="token keyword">int</span> cantidadValores <span class="token operator">=</span> <span class="token number">1000000</span><span class="token punctuation">;</span> 
        ArrayList<span class="token operator">&lt;</span>Integer<span class="token operator">&gt;</span> lista2 <span class="token operator">=</span> <span class="token keyword">new</span> <span class="token class-name">ArrayList</span><span class="token operator">&lt;</span><span class="token operator">&gt;</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
        startTime <span class="token operator">=</span> System<span class="token punctuation">.</span><span class="token function">nanoTime</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
        <span class="token keyword">for</span> <span class="token punctuation">(</span><span class="token keyword">int</span> i <span class="token operator">=</span> <span class="token number">0</span><span class="token punctuation">;</span> i <span class="token operator">&lt;</span> cantidadValores<span class="token punctuation">;</span> i<span class="token operator">++</span><span class="token punctuation">)</span><span class="token punctuation">{</span>
            lista2<span class="token punctuation">.</span><span class="token function">add</span><span class="token punctuation">(</span>i<span class="token operator">+</span><span class="token number">1</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
        <span class="token punctuation">}</span>
        duration <span class="token operator">=</span> System<span class="token punctuation">.</span><span class="token function">nanoTime</span><span class="token punctuation">(</span><span class="token punctuation">)</span> <span class="token operator">-</span> startTime<span class="token punctuation">;</span>
        System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">println</span><span class="token punctuation">(</span>String<span class="token punctuation">.</span><span class="token function">format</span><span class="token punctuation">(</span><span class="token string">"Inserción en ArrayList %,d"</span><span class="token punctuation">,</span> duration<span class="token operator">/</span><span class="token number">1000</span> <span class="token punctuation">)</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
        
        startTime <span class="token operator">=</span> System<span class="token punctuation">.</span><span class="token function">nanoTime</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
        lista2<span class="token punctuation">.</span><span class="token function">contains</span><span class="token punctuation">(</span><span class="token number">500000</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
        duration <span class="token operator">=</span> System<span class="token punctuation">.</span><span class="token function">nanoTime</span><span class="token punctuation">(</span><span class="token punctuation">)</span> <span class="token operator">-</span> startTime<span class="token punctuation">;</span>
        System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">println</span><span class="token punctuation">(</span>
            String<span class="token punctuation">.</span><span class="token function">format</span><span class="token punctuation">(</span><span class="token string">"Buscando el elemento del medio en ArrayList %,d"</span><span class="token punctuation">,</span>
                duration<span class="token operator">/</span><span class="token number">1000</span> <span class="token punctuation">)</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
        
        startTime <span class="token operator">=</span> System<span class="token punctuation">.</span><span class="token function">nanoTime</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
        lista2<span class="token punctuation">.</span><span class="token function">contains</span><span class="token punctuation">(</span><span class="token number">1000000</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
        duration <span class="token operator">=</span> System<span class="token punctuation">.</span><span class="token function">nanoTime</span><span class="token punctuation">(</span><span class="token punctuation">)</span> <span class="token operator">-</span> startTime<span class="token punctuation">;</span>
        System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">println</span><span class="token punctuation">(</span>
            String<span class="token punctuation">.</span><span class="token function">format</span><span class="token punctuation">(</span><span class="token string">"Buscando el último elemento en ArrayList %,d"</span><span class="token punctuation">,</span>
                duration<span class="token operator">/</span><span class="token number">1000</span> <span class="token punctuation">)</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
                
        startTime <span class="token operator">=</span> System<span class="token punctuation">.</span><span class="token function">nanoTime</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
        lista2<span class="token punctuation">.</span><span class="token function">contains</span><span class="token punctuation">(</span><span class="token number">10000000</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
        duration <span class="token operator">=</span> System<span class="token punctuation">.</span><span class="token function">nanoTime</span><span class="token punctuation">(</span><span class="token punctuation">)</span> <span class="token operator">-</span> startTime<span class="token punctuation">;</span>
        System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">println</span><span class="token punctuation">(</span>
            String<span class="token punctuation">.</span><span class="token function">format</span><span class="token punctuation">(</span><span class="token string">"Buscando elemento inexistente en ArrayList %,d"</span><span class="token punctuation">,</span>
                duration<span class="token operator">/</span><span class="token number">1000</span> <span class="token punctuation">)</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
                
        startTime <span class="token operator">=</span> System<span class="token punctuation">.</span><span class="token function">nanoTime</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
        lista2<span class="token punctuation">.</span><span class="token function">remove</span><span class="token punctuation">(</span><span class="token number">700000</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
        duration <span class="token operator">=</span> System<span class="token punctuation">.</span><span class="token function">nanoTime</span><span class="token punctuation">(</span><span class="token punctuation">)</span> <span class="token operator">-</span> startTime<span class="token punctuation">;</span>
        System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">println</span><span class="token punctuation">(</span>
            String<span class="token punctuation">.</span><span class="token function">format</span><span class="token punctuation">(</span><span class="token string">"Borrando elemento en ArrayList %,d"</span><span class="token punctuation">,</span>
                duration<span class="token operator">/</span><span class="token number">1000</span> <span class="token punctuation">)</span><span class="token punctuation">)</span><span class="token punctuation">;</span>                

        startTime <span class="token operator">=</span> System<span class="token punctuation">.</span><span class="token function">nanoTime</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
        lista2<span class="token punctuation">.</span><span class="token function">add</span><span class="token punctuation">(</span><span class="token number">0</span><span class="token punctuation">,</span> <span class="token operator">-</span><span class="token number">1</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
        duration <span class="token operator">=</span> System<span class="token punctuation">.</span><span class="token function">nanoTime</span><span class="token punctuation">(</span><span class="token punctuation">)</span> <span class="token operator">-</span> startTime<span class="token punctuation">;</span>
        System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">println</span><span class="token punctuation">(</span>
            String<span class="token punctuation">.</span><span class="token function">format</span><span class="token punctuation">(</span><span class="token string">"Insertando elemento en primera posicion en ArrayList %,d"</span><span class="token punctuation">,</span>
                duration<span class="token operator">/</span><span class="token number">1000</span> <span class="token punctuation">)</span><span class="token punctuation">)</span><span class="token punctuation">;</span>        
     <span class="token punctuation">}</span>
<span class="token punctuation">}</span>
</code></pre>
</div>
</body>

</html>
