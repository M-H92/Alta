<template>
  <section>
    <h1>
      Première création d'une
      <span class="db-tooltip" title="DataBase => Base de données">DB</span>
    </h1>
    <ol>
      <li>Introduction</li>
      <li>Créer une base de donnée</li>
      <li>Créer une table</li>
      <li>Ajouter des enregistrements</li>
      <li>Lire les enregistrements</li>
      <li>Conclusion</li>
    </ol>
    <h2>Introduction</h2>
    <p>
      Dans cette section, nous allons créer notre première
      <abbr class="db-tooltip tooltip" title="DataBase => Base de données">
        DB
      </abbr>
      "fatcatclinic" ayant pour but d'enregistrer le poids de votre animal de
      compagnie favoris <br />
      Nous verrons comment enregistrer et récupérer des données dans celle-ci et
      nous manipuleron pgAdmin pour la première fois <br />
      Notez bien que cette section ne fera qu'introduire les différents concepts
      de création, lecture, écriture... <br />
      Ceux-ci seront détaillés plus avant dans les prochaines sections
    </p>
    <h2>Créer une base de données</h2>
    <p>
      Lancez le programme pgAdmin et connectez vous. <br />
      À gauche se siture <strong>l'object explorer</strong> avec lequel vous
      pourrez facilement naviguer entre vos bases de données. <br />
      Naviguez dans celui-ci en ouvrant l'élément <strong>database</strong>.
      <br />
      Là, vous devriez voir une première base de données nommée
      <strong>postgre</strong> <br />
      À l'aide d'un clique droit sur cette dernière,, ouvrez le menu contextuel
      et sélectionnez l'option <strong>Query Tool</strong> <br />
      Le query tool vous permet d'écrire vos
      <strong title="requêtes" class="tooltip">queries</strong>
      <strong>SQL</strong> et ainsi de communiquer avec votre système de gestion
      de base de données.
    </p>
    <p>
      Dans le query tool, entrez la ligne de code suivante pour créer votre
      première base de données
    </p>
    <code lang="sql">CREATE DATABASE fatcatclinic;</code>
    <p>
      Pour ceux qui parlent un peu anglais, vous comprendrez rapidement ce dont
      il est question ici. <br />
      Nous <i>créons</i> une <i>base de données</i> dont le nom est
      fatcatclinic. Le <kbd>;</kbd> signifiant la fin de la requête sql <br />
      Avant d'exécuter ce code, remarquez aussi que certains mots sont colorés.
      <br />
      Il s'agit de mots clés spécifique au langage <strong>SQL</strong> et sont
      dit <i>réservés</i> <br />
      Ainsi, on ne nommera pas de base de données <i>DATABASE</i> ou encore
      <i>CREATE</i>
    </p>
    <p>
      Concluez la création de votre base de donnée en utilisant la touche
      <kbd>F5</kbd> ou en utilisant le bouton d'exécusion de requête représenté
      par un petit triangle et situé juste au dessus du query tool.
    </p>
    <p>
      Faites un clique droit sur l'objet <strong>database</strong> de
      <strong>l'explorateur d'objet</strong> et sélectionnez l'option
      <strong>refresh</strong> pour voir s'affichez votre première base de
      données. <br />
      Félicitations
    </p>
    <h2>Créer une table</h2>
    <p>
      Pour fonctionner, votre
      <abbr class="db-tooltip" title="DataBase => Base de données">DB</abbr> va
      avoir besoin de <strong>tables</strong>.
    </p>
    <p>
      Une table est une <strong>collection de données structurées</strong>.
      C'est à dire, un tableau dans lequel ranger vos données.
    </p>
    <p>
      Dans une table, on pourra parler de <strong>colonnes</strong> définissant
      le <strong>type de donnée</strong> et de
      <strong>rangées</strong> représentant chacunes un enregistrement de
      données.
    </p>
    <p>
      Pour bien comprendre, nous allons créer une table de pesée
      <i>weight</i> dans la base de données fatcatclinic.
    </p>
    <p>
      D'abord pensez aux données nécessaires pour garder un oeil à l'évolution
      du poids d'un chat. Un bon début sera de prendre note du poids et de la
      date de pesée. Nous aurons donc deux colonnes : <i>weight</i> (poids) et
      <i>date</i>
    </p>
    <h2>Ajouter des enregistrements</h2>
    <h2>Lire les enregistrements</h2>
  </section>
</template>
