<template>
  <section>
    <h1>
      Première
      <abbr class="db-tooltip tooltip" title="DataBase => Base de données"
        >DB</abbr
      >
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
      "fat_cat_clinic" ayant pour but d'enregistrer le poids de votre animal de
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
      À l'aide d'un clique droit sur cette dernière, ouvrez le menu contextuel
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
    <code lang="sql">CREATE DATABASE fat_cat_clinic;</code>
    <p>
      Pour ceux qui parlent un peu anglais, vous comprendrez rapidement ce dont
      il est question ici. <br />
      Nous <i>créons</i> une <i>base de données</i> dont le nom est
      fat_cat_clinic. Le <kbd>;</kbd> signifiant la fin de la requête sql <br />
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
      Faites un clique droit sur 'objet <strong>database</strong> de
      <strong>l'explorateur d'objet</strong> et sélectionnez l'option
      <strong>refresh</strong> pour voir s'affichez votre première base de
      données. <br />
      Félicitations
    </p>
    <h2>Crée une table</h2>
    <p>
      Pour fonctionner, votre
      <abbr class="db-tooltip" title="DataBase => Base de données">DB</abbr> va
      avoir besoin de <strong>tables</strong>.
    </p>
    <p>
      Une table est une <strong>collection de données structurées</strong>.
      C'est à dire, un tableau dans lequel ranger vos données selon une
      structure définie en amont.
    </p>
    <p>
      Dans une table, on pourra parler de <strong>colonnes</strong> qui seront
      nommées et définiront, entre autre, le <strong>type de donnée</strong>
      <br />
      et de <strong>rangées</strong> représentant chacunes un enregistrement de
      données au format précisé par les colonnes.
    </p>
    <p>
      Pour bien comprendre, nous allons créer une table dans la base de données
      fat_cat_clinic. Le but de cette table sera d'enregistrer régulièrement les
      pesées de notre animal. Nous allons donc nommer cette table
      <i>weight</i> et réfléchir eux données nécessaires pour garder un oeil à
      l'évolution du poids d'un chat.
    </p>
    <p>
      Un bon début sera de prendre note du poids et de la date de pesée. Nous
      aurons donc deux colonnes :
      <i>weight</i> (poids) et <i>date</i>.
    </p>
    <p>
      En plus de définir le nom de ces colonnes, il est nécessaire d'en définir
      le type. Pour le poids, nous utiliserons le type
      <strong>decimal</strong> permettant d'encoder des nombres décimaux en
      spécifiant la précision souhaitée. Pour la date, nous utiliserons le type
      <strong>date</strong> permettant d'encoder des... dates.
    </p>
    <p>
      Il existe et nous utiliserons d'autres types dans ce cours. Vous pouvez
      trouver une référence complète sur les types disponibles en suivant
      <a href="https://www.postgresql.org/docs/current/datatype.html">
        ce lien vers la documentation officielle </a
      >.
    </p>
    <p>
      Pour l'instant, vous pouvez vous contentez de lire, comprendre, copier et
      éxecuter le code ci-dessous dans le <strong>query tool</strong> de
      <strong>pgAdmin</strong>
    </p>
    <code lang="sql">
      USE fat_cat_clinic; <br />
      CREATE TABLE weight( <br />
      &nbsp;&nbsp;weight decimal(3,1), <br />
      &nbsp;&nbsp;date date <br />
      );
    </code>
    <p>
      Détaillons ensemble ce code : <br />
      <code lang="sql">USE fat_cat_clinic;</code> permet de spécifier quelle
      base de données utiliser. Si vous ouvrez le
      <strong>query tool</strong> via la base de données ciblée, cette portion
      de code n'est pas nécessaire. Néanmoins, n'étant pas problèmatique et
      permettant de se prémunir d'éventuelles erreurs, il sera de bon goût de
      l'utiliser <br />
      <code lang="sql">CREATE TABLE weight(</code> permet, vous l'aurez compris,
      de créer une <strong>table</strong> dont le nom sera <i>weight</i> la
      parenthèse permet de spécifier ce que contiendra cette table <br />
      <code lang="sql">weight decimal(3,1)</code> permet de créer, dans la table
      weight, une colonne weight de type décimal. Beaucoup de déclaration de
      type demandent des informations complémentaires. Dans le cas de decimal,
      il est possible de spécifier entre parenthèses la précision (le nombre de
      chiffres dans le nombre) et l'échelle (le nombre de chiffres derrière la
      virgule) souhaitée. Ainsi, decimal(3,1) nous permettra d'encoder des poids
      en kg avec une précision à l'hectogramme et allant jusqu'à 99,9 kg. Nous
      devrions être bon pour nos chats. <br />
      <code lang="sql">date date</code> permet de comme la ligne précédente de
      créer une colonne. Celle-ci sera de type date <br />
      N'oubliez pas de fermer la parenthèse et d'ajouter un <kbd>;</kbd>
    </p>
    <h2>Ajouter des enregistrements</h2>
    <p>
      Maintenant que notre <srong>table</srong> weight est créée, nous allons la
      <span
        title="Du wiktionnaire : (Bases de données) Alimenter (une table, une base de données) en informations."
      >
        populer
      </span>
      avec quelques informations.
    </p>
    <p>
      Comme pour le point précédent, lisez attentivement ce code et exécutez le
    </p>
    <code lang="sql">
      INSERT INTO weight (weight, date) <br />
      &nbsp;&nbsp;VALUES (3.5, '2024-01-19');
    </code>
    <p>
      <code lang="sql">INSERT INTO weight</code> permet d'insérer des données
      dans la table weight
    </p>
    <p>
      Les informations entre parenthèses
      <code lang="sql">(weight, date)</code> permettent de spécifier quelles
      valeurs seront insérées et dans quel ordre. <br />
      Cette information pourrait être omise tant que les valeurs insérées sont
      écrites dans l'ordre des colonnes de la table ciblée. <br />
      Néanmoins, inclure cette information permet, entre autres, d'éviter
      d'éventuelles erreurs. Je vous invite donc à ajouter systématiquement
      cette information.
    </p>
    <p>
      Le mot clé <code lang="sql">VALUES</code> précède les données à insérer
      qui sont reprises entre parenthèses
      <code lang="sql"> (3.5, '2024-01-19') </code>. Notez que la date est
      entourées de <kbd>'</kbd> et au format
      <i title="years-month-day respectivement sur 4, 2 et 2 chiffres">
        yyyy-MM-dd
      </i>
    </p>
    <p>
      Pour bien faire, nous allons ajouter quelques données supplémentaires avec
      le code suivant :
    </p>
    <code>
      INSERT INTO weight (weight, date) <br />
      &nbsp;&nbsp; VALUES (3.6, '2024-08-03')<br />
      &nbsp;&nbsp;&nbsp;&nbsp;,(3.7, '2024-07-06') <br />
      &nbsp;&nbsp;&nbsp;&nbsp;,(3.5, '2024-06-01') <br />
      &nbsp;&nbsp;&nbsp;&nbsp;,(3.6, '2024-05-04') <br />
      &nbsp;&nbsp;&nbsp;&nbsp;,(3.4, '2024-04-06') <br />
      &nbsp;&nbsp;&nbsp;&nbsp;,(3.4, '2024-03-02') <br />
      &nbsp;&nbsp;&nbsp;&nbsp;,(3.5, '2024-02-03');
    </code>
    <p>Ici, la même commande est utilisée pour insérer une série de données.</p>
    <h2>Lire les enregistrements</h2>
    <p>
      Maintenant que nous avons créé une base de données, créé une table et
      inséré une série de données, nous pouvons commencer à lire celles-ci. Nous
      allons donc en profiter pour faire quelques requêtes.
    </p>
    <p>
      La première, ci-dessous, va nous permettre de lire les informations
      contenues dans la table
    </p>
    <code lang="sql"> SELECT weight, date FROM weight; </code>
    <p>
      Les deux mots clés à retenir ici sont <code lang="sql">SELECT</code> et
      <code lang="sql">FROM</code>. <br />
      <code lang="sql">SELECT</code> sera suivi des colonnes à récupérer. Vous
      pourriez donc ne sélectionner que les poids avec une requête
      <code lang="sql">SELECT weight FROM weight;</code> <br />
      <code lang="sql">FROM</code> permet de spécifier la table dans laquelle
      récupérer les données.
    </p>
    <p>Une seconde version de cette requête sera la suivante</p>
    <code lang="sql">SELECT * FROM weight;</code>
    <p>
      Ici, le symbole <kbd>*</kbd> sera utilisé comme <i>joker</i> pour
      signifier <i>toutes les colonnes</i>. <br />
      Pratique pour les tests, mais à ne pas utiliser de manière systématique
      dans vos projets de développement. Nous en reparlerons plus tard.
    </p>
    <p>
      Pour voir l'évolution dans le temps du poids du chat observé, il serait
      intéressant de trier les résultats par date. <br />
      Bonne nouvelle, c'est possible avec la paire de mots clés
      <code lang="sql">ORDER BY</code>.
    </p>
    <code lang="sql">
      SELECT * FROM weight <br />
      ORDER BY date;
    </code>
    <p>
      Il sera même possible de choisir l'ordre du tri en ajoutant soit
      <code lang="sql">ASC</code> ou <code lang="sql">DESC</code> après notre
      <code lang="sql">ORDER BY</code>
    </p>
    <code lang="sql">
      SELECT * FROM weight <br />
      ORDER BY date DESC;
    </code>
    <p>
      Pratique ! Et cela ne s'applique pas qu'aux dates ! Même si dans notre
      cas, trier par poids semble moins pertinent, je vous invite à essayer.
    </p>
    <h2>Conclusion</h2>
    <p>
      Dans cette section, vous avez eu appris à créer une base de données, créer
      une table, insérer des enregistrements et enfin, lire des enregistrements.
    </p>
    <p>
      Vous avez appris comment définir les types des données lors de la création
      de tables et aussi comment modifier une requête de lecture .
    </p>
    <p>
      Ces différents concepts seront approfondis dans les prochaines sections
    </p>
  </section>
</template>
