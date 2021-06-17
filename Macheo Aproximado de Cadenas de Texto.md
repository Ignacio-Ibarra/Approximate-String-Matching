# Macheo Aproximado de Cadenas de Texto

En este repo implmenté el algoritmo TF-IDF (_Term Fecuency, Inverse Document Fecuency_) junto con _cossine simmilarity_ para poder realizar una limpieza de un dataset que contenía 
nombres de empresas extranjeras que realizaron ventas a empresas importadoras argentinas. 

El dataset contenía inicialmente +11M de registros. Con Spark se logró obtener alrededor de 2M de [registros únicos sucios](https://github.com/Ignacio-Ibarra/Approximate-String-Matching/blob/main/Valores_Sucios_Unicos.ipynb).

Luego de una [limpieza utilizando expresiones regulares](https://github.com/Ignacio-Ibarra/Approximate-String-Matching/blob/main/Limpieza_Regex.ipynb), se realizó la vectorización
mediante la separación de cada documento en tri-gramas para todas las palabras del documentos que no pertenecieran a una lista de palabras comunes 
(tales como LTD, CORP, CORPORATION, SA, LIMITED, BRASIL, INDUSTRIAL, INDUSTRY, etc). Las palabras que sí pertenecían a la lista fueron incorporadas al 
vocabulario del vectorizador sin separar en tri-gramas.

El vectorizador de TF-IDF utilizó como input el vocabulario antes armado y los documentos. Generando una vectorización de alrededor de 500K documentos. 
Luego para evaluar la similitud entre vectores se utilizó la similitud del coseno, por ser simplemente un producto matricial (ver explicación [aquí](https://github.com/Ignacio-Ibarra/Approximate-String-Matching/blob/main/Approximate_String_Matching_using_TF_IDF_over_Large_Dataset_Explanation.ipynb)). 
El resultado de dicho [proceso](https://github.com/Ignacio-Ibarra/Approximate-String-Matching/blob/main/TFIDF_String_Matching.ipynb) fue la reducción a 290K registros de empresas distintas. 

Aún hay espacio para mejorar... pero como trabajo inicial es bastante bueno. Cualquier colaboración o mejora no duden en contactarme por este medio. 



