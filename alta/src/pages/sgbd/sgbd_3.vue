<template>
  <section>
    <h2>Contraintes</h2>
    <p>
      Quand nous avions ajouté le nom de l'animal à notre table, nous avions eu
      un problème de <i>null</i>. <br />
      Petit rappel, null représente, pour un colonne d'un record, qu'il n'y a
      pas de données
    </p>
    <p>
      Ceci nous avais contraint à modifier nos données via une requête
      <i>UPDATE</i> avec l'utilisation d'un <i>WHERE</i> et, heureusement, la
      différence de poids entre mon chat et celui de ma belle soeur était telle
      qu'une clause where sur le poids de nos animaux avait suffit à discerner
      nos animaux
    </p>
    <p>
      Néanmoins, à l'avenir, avec plus de chats ou de pesées, ça pourrait ne
      plus suffire.
    </p>
    <p>
      Nous allons donc nous prémunire de ce problème avec une
      <strong>constraint</strong>
    </p>
    <p>
      Une <i>constraint</i> est, comme son nom l'indique, une contrainte que
      l'on peut appliquer, par exemple, sur notre colonne <i>cat</i> pour
      interdire les valeurs nulles. Appliquons la avec le code suivant :
    </p>
    <code> ALTER TABLE weight ALTER COLUMN cat SET NO NULL; </code>
    <p>
      Pas de surprise ici. Les différents mot-clés sont presque tous connus
      <br />
      Nous <i>alterons</i> la <i>table</i> <i>weight</i> pour laquelle nous
      <i>alterons</i> la <i>colonne</i> <i>cat</i> <br />
      Pour cette colonne, nous spécifions qu'elle ne peut pas contenir la valeur
      <i>null</i> avec <strong>SET NO NULL</strong>
    </p>
    <p>
      Tant que nous y somme, posons nous la question : est-ce qu'une pesée sans
      poids peut avoir du sens? quid d'une pesée non datée? Ajoutons aussi les
      contraintes <i>NO NULL</i> pour ces deux colonnes
    </p>
    <p>
      Vous avez peut-être essayé de mettre la contrainte <i>NO NULL</i> alors
      que votre colonne contenait déjà des valeurs nulles. <br />
      Non? <br />
      Essayez-donc pour voir le résultat <br />
      Essayez aussi d'insérer des valeurs nulles maintenant que les contraintes
      sont appliquées
    </p>
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
