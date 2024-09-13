<template>
  <section>
    <h1>Relations</h1>
    <ol>
      <li>Introduction</li>
      <li>Fonctions</li>
      <li>ALTER et UPDATE</li>
      <li>WHERE</li>
      <li>Clé primaire</li>
      <li>Clé étrangères et relations</li>
      <li>WHERE suite</li>
      <li>Conclusion</li>
    </ol>
    <hr />
    <!-- Ajouter un nom au chat
     Ajouter des records
     Prendre tout et trier par chat
     Prendre pour un chat
     Prendre le dernier pour un chat
     Prendre le dernier pour chaque chat
     Est-ce que ça fait beaucoup? 
     Pour s'en rendre compte
     Ajouter race
     Ajouter date naissance
     Ajouter sexe 
    -->
    <h2>Introduction</h2>
    <!--  -->
    <h2>Fonctions</h2>
    <p>
      Le simple fait de récupérer des données rend déjà les
      <abbr class="db-tooltip" title="DataBase => Base de données">DB</abbr>
      très puissantes. Mais elles peuvent faire plus que ça. Entre autres, elles
      peuvent déjà traiter la donnée
    </p>
    <p>
      Dans notre cas, nous allons essayer de récupérer le poids maximal de notre
      chat dans la table weight de la
      <abbr class="db-tooltip" title="DataBase => Base de données">DB</abbr>
      fat_cat_clinic. <br />
      Pour ce faire, nous allons utiliser une <strong>fonction</strong>.
    </p>
    <p>
      Vous avez certainement déjà entendu parler de
      <strong>fonctions</strong> dans votre cours de programmation. Si ce n'est
      le cas, voyez ça pour l'instant comme des moyens d'obtenir de nouvelles
      fonctionnalités. Le concept sera détaillé dans le cours adéquat.
    </p>
    <p>
      Une fonction s'utilise en l'appelant par son nom et en spécifiant entre
      parenthèses, des <strong>arguments</strong>.
    </p>
    <p>
      Selon la fonction, les arguments disposent de rôles différents. Ici, nous
      allons utiliser la fonction <code lang="sql">MAX(argument)</code> <br />
      Cette fonction est une <strong>fonction d'aggrégation</strong> et permet
      de retourner le "maximum" pour les données d'une colonnes spécifiées en
      argument
    </p>
    <p>Essayez le code suivant</p>
    <code lang="sql"> SELECT MAX(weight) FROM weight; </code>
    <p>
      Vous devriez obtenir le poids maximum de notre chat. <br />
      Notez que la colonne retournée ne dispose pas d'un nom très explicite.
      <br />
      Vous pouvez la renommer avec un <strong>alias</strong> grâce au mot clé
      <code lang="sql">AS</code>. Essayez donc ceci :
    </p>
    <code lang="sql"> SELECT MAX(weight) AS max_weight FROM weight</code>
    <p>C'est tout de même plus clair !</p>
    <p>
      En vrac, voici quelques autres fonctions d'aggrégation : MIN, MAX,
      <abbr title="Average => moyenne">AVG</abbr>,
      <abbr title="Somme">SUM</abbr>, COUNT. <br />
      Une liste plus complète est disponible
      <a href="https://www.postgresql.org/docs/16/functions-aggregate.html">
        ici
      </a>
    </p>
    <p>
      Essayez donc d'afficher le poids moyen de notre chat avant de passer au
      prochain point. Quelque chose devrait vous gêner dans l'affichage des
      résultats et je vous conseille vivement d'aller voir le lien cité plus
      haut pour résoudre ce problème
    </p>
    <h2>Alter</h2>
    <p>
      Pour l'instant, tout fonctionne comme prévu. Mais nous allons rapidement
      changer ça en ajoutant quelques enregistrement de poids pour un autre chat
      dans notre base de données. <br />
      Pas de problèmes. Vous savez déjà comment faire ! Un petit coup d'<code
        lang="sql"
        >INSERT</code
      >
      et le tour est joué... <br />
      Sauf qu'il s'agit d'un maine coon pouvant atteindre jusqu'à 8kg en temps
      normal. <br />
      D'un seul coup plus moyen de distinguer un enregistrement très inquiétant
      en rapport avec le poids de votre chat d'un enregistrement tout à fait
      normal pour un maine coon...
    </p>
    <p>
      Si nous avions pensé à ce problème avant de créer notre table, nous
      aurions certainement ajouté une colonne permettant de distinguer de quel
      chat il s'agit. Par exemple <i>name</i> ou <i>cat</i><br />
      Heureusement pour nous, pas besoin de supprimer notre table et toutes les
      données enregistrées pour recréer une table avec cette colonne
      supplémentaire <br />
      Effectivement, il est possible de modifier la définition d'une table grâce
      à la commande <code lang="sql">ALTER</code>. <br />
      Essayez donc ce code :
    </p>
    <code lang="sql">
      ALTER TABLE weight <br />
      &nbsp;&nbsp;ADD cat varchar(32);
    </code>
    <p>
      Ce code permet <i>d'altérer</i> la table weight pour y ajouter une colonne
      nommée <i>car</i> de type <strong>varchar</strong>
    </p>
    <p>
      Le type <strong>varchar</strong> permet de stocker du texte d'un nombre de
      caractères allant jusqu'au nombre précisé lors de la définition de la
      colonne. Plus d'info via
      <a href="https://www.postgresql.org/docs/current/datatype-character.html">
        ce lien
      </a>
    </p>
    <p>
      Sélectionnez toutes les informations de la table weight pour vérifier que
      cela ai bien fonctionné... Et voyez un résultat surprenant... <br />
      La colonne <i>cat</i> est remplie de l'information
      <strong>[null]</strong>. <br />
      Rassurez vous, c'est normal ! <i>null</i> signifie simplement qu'il n'y a
      pas de données. <br />
      Nous n'avons effectivement jamais renseigné de nom pour nos
      enregistrements de poids jusqu'à présent vu que la colonne n'existait pas.
    </p>
    <p>Corrigeons ce problème avec le bout de code suivant :</p>
    <code lang="sql">
      UPDATE weight <br />
      SET cat = 'Monza';
    </code>
    <p>
      Pour ceux qui ont fait un peu d'anglais, vous comprendrez vite que le mot
      clé <code lang="sql">UPDATE</code> permet de <strong>modifier</strong> les
      valeurs contenues dans une table. <br />
      Le mot clé <code lang="sql">SET</code> permet de spécifier la colonne
      ainsi que la valeur à attribuer à celle-ci. <br />
      Notez encore la mention <i>Monza</i> écrite entre des <kbd>'</kbd>. <br />
      Il s'agit du nom de mon chat et est écrit entre apostrophes car il s'agit
      d'une <span class="tooltip" title="chaine de caractère">string</span>.
      <br />
      D'une manière générale, vous croiserez souvent les textes entourés par des
      <kbd>'</kbd> ou bien <kbd>"</kbd>
    </p>
    <p>
      Sélectionnez à nouveau les informations de la table <i>weight</i> pour
      voir que chaque enregistrement est maintenant au nom de <i>Monza</i>
    </p>
    <!-- <h2>WHERE</h2> -->
    <!-- Ajouter des chats et filtrer sur chats -->
    <!-- <h2>Clé primaire</h2> -->
    <!-- Nouvelle table de chats avec clé primaire -->
    <!-- <h2>Clé étrangères et relations</h2> -->
    <!-- Clé étrangère correspondante -->
    <!-- <h2>WHERE suite</h2> -->
    <!-- Amélio -->
    <!-- <h2>Conclusion</h2> -->
  </section>
</template>
