## Romanian-sub-dialect-identificator
Discriminate between the Moldavian and the Romanian dialects across different text genres.

### Importarea librăriilor
Pentru realizarea proiectului am folosit urmatoarele librării:  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;• **pandas**: pentru citirea fișierelor și încărcarea datelor  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;• **sklearn**: pentru importarea modelului, modelarea datelor și determinarea matricei de confuzie și scorului f1  


### Citirea datelor
Citirea datelor s-a realizat prin intermediul funcției pd.read_csv cu următorii parametrii:  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;• calea pentru fișierele txt cu datele de antrenare, validare și test  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;• sep: separatorul folosit între date  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;• header: fișierele nu conțin header  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;• engine: python  
Valorile citite sunt introduse într-un data frame ca mai apoi să fie convertit la un vector din NumPy prin intermediul funcției .to_numpy()  

### Definirea modelului
Am folosit modelul **SVM** din biblioteca **ScikitLearn** pentru a face diferența dintre cuvintele ce aparțin dialectului românesc sau dialectului moldovenesc.  
Parametrul **C** a fost setat la valoarea **23** pentru că s-a observat că la valori mai mari s-a ajuns la supraînvățare.  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Parametrul **kernel** a fost setat la valoarea defaut **(‘linear’)**  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Parametrul **gamma** a fost setat la valoarea **110**.  
Pentru obținerea valorilor numerice din test_samples am folosit clasa TfidfVectorizer.  

### Normalizarea datelor
Funcția normalize_data(train_data, test_data, type='l2') primește ca parametri datele de antrenare, datele de testare și respectiv tipul de normalizare inițializat implicit cu valoarea l2 care intoarce datele normalizate.

### Exportarea datelor
Pentru a genera predicția pentru datele de test și exportarea în format CSV am folosit DataFrame din pandas și .to_csv() cu parametrul index = false pentru a nu numerota rândurile din fișierul cu predicții.
