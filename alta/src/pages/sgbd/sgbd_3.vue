<template>
  <section>
    <h2>Problème de poids</h2>
    <p>
      Pour profiter des capacités de notre base de données à traiter la donnée
      lors de la récupération, nous allons ajouter quelques informations de
      <strong>référence</strong> dans notre table.
    </p>
    <p>En vrac :</p>
    <ul>
      <li>Le poids moyen vers lequel devrait tendre notre chat</li>
      <li>La race de notre chat</li>
      <li>Son sexe</li>
      <li>Son âge</li>
      <li>S'il est stérilisé</li>
    </ul>
    <p>
      Si nous ajoutons toutes ces informations notre table weight, nous nous
      retrouvons avec ce genre de résultat
    </p>
    <table>
      <thead>
        <tr>
          <th>weight</th>
          <th>date</th>
          <th>cat</th>
          <th>ideal_weight</th>
          <th>race</th>
          <th>is_male</th>
          <th>age</th>
          <th>is_sterilised</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <td>3.5</td>
          <td>'2024-02-02'</td>
          <td>'Monza'</td>
          <td>6.5</td>
          <td>'Persan'</td>
          <td>true</td>
          <td>7</td>
          <td>true</td>
        </tr>
        <tr>
          <td>3.6</td>
          <td>'2024-03-04'</td>
          <td>'Monza'</td>
          <td>6.5</td>
          <td>'Persan'</td>
          <td>true</td>
          <td>7</td>
          <td>true</td>
        </tr>
        <tr>
          <td>3.5</td>
          <td>'2024-04-02'</td>
          <td>'Monza'</td>
          <td>6.5</td>
          <td>'Persan'</td>
          <td>true</td>
          <td>7</td>
          <td>true</td>
        </tr>
        <tr>
          <td>3.6</td>
          <td>'2024-05-10'</td>
          <td>'Monza'</td>
          <td>6.5</td>
          <td>'Persan'</td>
          <td>true</td>
          <td>7</td>
          <td>true</td>
        </tr>
        <tr>
          <td>3.7</td>
          <td>'2024-06-08'</td>
          <td>'Monza'</td>
          <td>6.5</td>
          <td>'Persan'</td>
          <td>true</td>
          <td>7</td>
          <td>true</td>
        </tr>
      </tbody>
    </table>
    <p>
      prennez un peu de temps pour regarder ces données et remarquons quelque
      chose...
    </p>
    <p>
      Nous avons beaucoup de <strong>répétitions</strong> et cela est un
      problème.
    </p>
    <p>
      Tout d'abord, nous devons maintenant ajouter ces informations lors de
      l'insertion de chaque record dans notre table <i>weight</i>. <br />
      Non seulement, cela va nous prendre plus de temps, mais en plus, c'est une
      source d'erreur potentielle ! <br />
      Que faire quand mon chat sera une fois de race <i>persan</i> et une autre
      de race <i>maine coon</i> ? Quelle information conserver ?
    </p>
    <p>
      Ensuite, nous augmentons considérablement le poids de chaque record pour
      des informations qui ne sont pas variables entre deux pesées (sauf pour
      l'âge et s'il est stérilisé. Nous reviendrons là-dessus plus tards) <br />
      Effectivement, nous passons d'un record avec 3 champs assez léger à un
      record de 8 champs ! <br />
      Et bien que ceux-ci ne soient pas individuellement trop lourd, le poids de
      ceux-ci se fera sentir lors de l'accumulation d'un plus grand nombre de
      records.
    </p>
    <p>
      Réflechissez a de potentielles solutions à ce problème de répétition de
      données avant de lire la suite. <br />
      Comment pourriez-vous résoudre ce problème si vous preniez des notes
      papier plutôt qu'en utilisant une base de données?
    </p>
    <h2>Relations</h2>
    <p>
      Je vous propose de résoudre ce problème en vous présentant le principe de
      relations dans une base de données
    </p>
    <p>
      Certains l'auront déjà remarqué ou entendu : on parle parfois de base de
      données relationnelles
    </p>

    <h2>Clé primaires</h2>
    <h2>Clé étrangères</h2>
    <h2>Jointures (introduction)</h2>
    <h2>Requêtes imbriquées (introductions)</h2>
    <h2>Tables de liaison</h2>
  </section>
</template>
<script></script>
