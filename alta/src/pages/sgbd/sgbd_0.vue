<template>
  <section>
    <h1>Préambule</h1>
    <ol>
      <li>Introduction</li>
      <li>Pourquoi une base de données</li>
      <li>Terminologies de base</li>
      <li>Installation</li>
      <li>Conclusion</li>
    </ol>
    <h2>Introduction</h2>
    <p>
      Dans cette section, nous allons voir le but de l'ajout d'une
      <abbr class="db-tooltip" title="DataBase => Base de données">DB</abbr>
      à votre projet de développement ainsi que quelques mots de vocabulaire de
      base. <br />
      Nous téléchargerons aussi les programmes nécessaire pour la suite de ce
      cours
    </p>
    <h2>Pourquoi une base de données</h2>
    <p>
      En tant que développeur, vous allez créer des systèmes remplissant trois
      rôles qui sont, au sens large
    </p>
    <ol>
      <li>Intégrer des donnée</li>
      <li>Manipuler des donnée</li>
      <li>Restituer des donnée</li>
    </ol>
    <p>Quelques exemples en vrac :</p>
    <p>Intégrer des données :</p>
    <ul>
      <li>
        Lors d'une inscription à un service web, récupération des informations
        d'un formulaire en ligne
      </li>
      <li>
        Lors de la génération d'une facture depuis un devis, lecture des
        fichiers de devis
      </li>
      <li>Dans un jeu vidéo, quelle touche est pressée</li>
    </ul>
    <p>Manipuler des données</p>
    <ul>
      <li>
        Validations des données d'un formulaire d'inscription (âge ok?
        complexité du mdp ok?)
      </li>
      <li>Calcul des montants d'une facture sur base du devis</li>
      <li>
        Quelle action doit réaliser le personnage, est-ce que son étât le lui
        permet? Quel résultat dans le monde
      </li>
    </ul>
    <p>Restituer des données</p>
    <ul>
      <li>
        Feedback utilisateur d'inscription réussie, affichage de ses données
        dans une page "profil"...
      </li>
      <li>Envoi de la facture vers une imprimante</li>
      <li>
        Affichage de la prochaine frame à l'écran correctement mise à jour
      </li>
    </ul>
    <p>
      Dans cette <strong>optique de gestion des données</strong>, une
      <abbr class="db-tooltip" title="DataBase => Base de données">DB</abbr>
      pourra être mise en place pour faire
      <strong>persister</strong> les données et les
      <strong>restituer</strong> plus tard...
    </p>
    <p>
      Tout comme il serait possible de le faire avec un fichier ou même un
      classeur et du papier...
    </p>
    <p>
      Il sera par conséquent important lors du processus d'analyse d'évaluer
      l'intérêt de la mise en place d'une
      <abbr class="db-tooltip" title="DataBase => Base de données">DB</abbr> en
      prenant en considération les avantages qu'elle apporte
    </p>
    <ul>
      <li>Récupération efficace et modulable de la donnée</li>
      <li>Gestion de la concurence lors du travail à plusieurs</li>
      <li>Sécurité sur l'accès en lecture et en écriture</li>
      <li>Accessibilité</li>
      <li>Manipulation de la donnée</li>
      <li>Périnité</li>
      <li>Récupération et systèmes de backup</li>
      <li>...</li>
    </ul>
    <p>
      Dans les cas précédents, il serait raisonnable d'imaginer l'utilisation
      d'une
      <abbr class="db-tooltip" title="DataBase => Base de données">DB</abbr>
      pour gérer les utilisateurs de son service ou les factures de son
      entreprise.
    </p>
    <p>
      il serait par contre difficilement justifiable d'en utiliser une pour
      sauvegarder les inputs d'un jeu vidéo qui sont des données à caractère
      plus volatil et destinées à être utilisées sur le moment.
    </p>
    <p>
      On peut imaginer d'autres cas d'utilisation comme une entreprise
      souhaitant accéder à ses résultats comptables sur plusieurs années pour en
      extrapoler des prévisions pour les années à venir, un institut
      météorologique récupérant quotidiennement les données météo pour aggréger
      des moyennes et autres statistiques, un établissement scolaire souhaitant
      garder une trace des résultats des étudiants pendant plusieurs années...
    </p>
    <h2>Installation</h2>
    <p>
      Pour ce cours, nous allons utiliser système de gestion de base de données
      <strong>postgreSQL</strong> ainsi que le logiciel <strong>pgAdmin</strong>
    </p>
    <p>
      Vous pouvez télécharger l'installeur pour ces deux éléments sur
      <a href="https://www.postgresql.org/download/">le site officiel</a> de
      postgreSQL. <br />
      Ce cours utilise la version 16.4 de postgre, mais rien ne vous empêche de
      prendre une version plus à jour. <br />
      Si à ce stade, vous n'êtes pas certain de pouvoir bien cerner les
      différences entre PostgreSQL, pgAdmin et SQL, je vous sugggère de lire la
      prochaine section pendant votre téléchargement.
    </p>
    <p>
      Lorsque votre téléchargement est terminé, vous devriez pouvoir lancer
      l'installeur et conserver les options par défaut. <br />
      Notez qu'il ne sera pas nécessaire pour ce cours de faire des
      installations supplémentaires via Stack builder
    </p>
    <p>
      Une fois installé, vérifiez que tout se soit bien passé en ouvrant le
      programme pgAdmin et en vous connectant au server grâce au mot de passe
      attribué pendant l'installation
    </p>
    <h2>Terminologies de base</h2>
    <p>
      <strong>Base de données relationnelle</strong>. Il s'agit d'un type de
      base de données impliquant des <strong>relations</strong> entre les
      différentes entités.
    </p>
    <p>
      <strong>Système de Gestion de Base de Données </strong>. Il s'agit du
      système permettant de gérer des base de données. MySQL, SQLServer, MariaDB
      ou PostGreSQL sont des systèmes de gestion de bases de données
      relationnelle
    </p>
    <p>
      <strong>SQL</strong> ou
      <span title="Langage de requête structuré">
        Structured Query Language
      </span>
      est le <strong>langage</strong> permettant de communiquer avec les bases
      de données.
    </p>
    <p>
      Logiciel de <strong>gestion et d'administration</strong> de base de
      données. Il s'agit de programmes permettant de manipuler les bases de
      données. MySQL Workbench, SQL Server Management Studio ou pgAdmin en sont
      des exemples
    </p>
    <p>
      Bien que ces éléments soient en essence bien distincts, une confusion
      apparait parfois au vu de la proximité des termes utilisés. Il est bien
      important de comprendre que...
    </p>
    <p>
      SQL est le <strong>langage</strong> qui sera utilisé... Aussi bien sur
      MySQL que sur SQL Server, postgreSQL,... (avec parfois de légères
      variations)
    </p>
    <p>
      Pour manipuler une base de données, un système de gestion de base de
      données sera nécessaire. <br />
      Le choix entre les différents concurent se fera selon les critères de
      prix, de compatilibité avec son projet de développement, d'efficacité, de
      philosophie (certains sont open source)
    </p>
    <p>
      La plupart des système de gestion de base de données disposent d'un
      logiciel permettant de manipuler les bases de données. <br />
      Bien que ces logiciels ne soient pas obligatoires, ils simplifient
      fortement l'utilisation d'une base de données. <br />
      Comme pour les systèmes de gestion de base de données, de multiples
      concurents existent et, bien souvent, les logiciels vont de paire avec un
      système particulier. <br />
      On aura par exemple MySQL avec MySQL Workbench par Oracle, SQL Server et
      SQL Server Management Studio par Microsoft, PostGreSQL et pgAdmin,...
    </p>
    <h2>Conclusion</h2>
    <p>
      Au terme de cette section d'introduction, vous devriez maintenant avoir
      une idée de l'intérêt que peut avoir une
      <abbr class="db-tooltip" title="DataBase => Base de données">DB</abbr>
      ainsi que de disposer de tout les outils nécessaires pour commencer à les
      manipuler. <br />
      Rendez-vous à la prochaine section pour ce faire
    </p>
  </section>
</template>

<script setup></script>
