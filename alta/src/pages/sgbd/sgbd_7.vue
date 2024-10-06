<template>
  <section>
    <h2>Propriétaires</h2>
    <p>
      Grâce aux modifications faites lors du dernier chapitre, nous pouvons
      maintenant savoir si un chat est en retard sur un vaccin ou connaitre la
      date de son prochain vaccin prévu.
    </p>
    <p>
      Nous pourrions profiter de ceci pour ajouter une fonctionnalité de
      messagerie à un programme qui utiliserait notre base de données, de telle
      sorte que, si un chat doit se faire vacciner, un message soit envoyé au
      propriétaire du chat.
    </p>
    <p>Ajoutons les informations des propriétaires.</p>
    <p>
      D'abord, définissons le type de relation entre un chat et un propriétaire.
    </p>
    <p>
      Un chat devra avoir strictement un propriétaire. <br />
      Un chat n'ayant pas de propriétaire ne verra jamais son poids encodé dans
      notre base de données et, si une SPA ou autre souhaite référencer des
      chats, elle pourra être encodée comme un "propriétaire". <br />
      Nous pourrions envisager d'ajuster la base de données pour qu'un chat
      puisse avoir plusieurs propriétaires. <br />
      Ce ne serait pas du tout illogique, mais ce n'est pas réellement
      nécessaire pour notre cas d'utilisation (envoyer un message à
      l'utilisateur). <br />
      Il revient donc au développeur de faire le choix qui l'intéresse le plus.
    </p>
    <p>
      Par contre, un propriétaire pourra avoir plusieurs chats. <br />
      Je vais donc me retrouver dans un type de relation <i>One to Many</i>
    </p>
    <p>
      Ensuite, définissons les informations nécessaires dans cette table de
      propriétaires.
    </p>
    <p>
      Pour pouvoir facilement les rentrouver, un nom et un prénom seront
      utilisés <br />
      Pour être certain de les différenciers en base de données, un pseudo sera
      attribué. <br />
      À la différence d'un nom/prénom, le pseudo sera strictement unique et
      pourra faire office de <i>PK</i><br />
      Un id numérique auto incrémenté pourrait être utilisé, mais un pseudo sera
      plus parlant <br />
      Pour les contacter, il nous faudrait : <br />
      un numéro de téléphone portable pour envoyer des sms <br />
      ou une adresse mail <br />
      ou encore une adresse postale pour envoyer l'information par courrier
      <br />
      Plutôt que de faire un choix parmis les trois options, nous allons
      récolter toutes ces informations.
    </p>
    <p>
      Par contre, autant le poids d'un chat n'est pas une données très sensible,
      autant il pourrait être intéressant de limiter l'accès aux informations de
      contacte des différents propriétaires... <br />
      Nous allons donc utiliser un nouveau type de relation qui pourrait nous
      être utile
    </p>
    <h2>One to One</h2>
    <p>
      La relation one to one est un peu particulière en ce sens qu'elle ne
      semble, au premier abord, ne pas apporter beaucoup plus de possibilités
      qu'un ajout de champs dans une table unique. <br />
      Effectivement, pourquoi ajouter une table pour le numéro de téléphone et
      une adresse mail quand je pourrais simplement ajouter deux colonnes dans
      ma table et ne pas me compliquer la vie avec des jointures? <br />
      Cinq réponses classiques se présentent généralement : <br />
    </p>
    <ol>
      <li>La sécurité</li>
      <li>La spécificité</li>
      <li>La performance</li>
      <li>La concurrence</li>
      <li>La lisibilité</li>
    </ol>
    <p>
      La sécurité : il est possible de séparer les droits d'accès aux
      différentes tables SQL. Néanmoins, ce point ne sera pas détaillé dans
      cette partie du cours. Il faudra attendre votre cours de base de données
      de deuxième année. <br />
      Par exemple, ne laisser les droits d'accès à cette table de contactes qu'à
      notre application de rappel de vaccin.
    </p>
    <p>
      La spécificité : d'un cas générique peut découler plusieurs cas
      spécifiques. On pourra alors séparer la donnée en groupant les éléments
      génériques et en spécifiant un lien vers un table spécifique les cas
      échéants. <br />
      Par exemple, une table <i>Personne</i> qui pourra être lié à une table
      <i>Etudiant</i> ou <i>Professeur</i>.
    </p>
    <p>
      La performance : dans le cas de <i>Full table scan</i>, on souhaitera
      avoir moins de colonnes. (Le gain de performance réel est néanmoins à
      relativiser par rapport au fait d'écrire une requête correcte)
    </p>
    <p>
      La concurrence : une table / un record peut être verrouillé lors
      d'opérations en écriture. Ceci posant problème quand plusieurs personnes
      tentent de modifier une information dans le même enregistrement. <br />
      Si la donnée est séparé en plusieurs tables, le problème sera moins
      présent. <br />
      (À noter toutefois que la plupart des SGDB modernes disposent déjà de
      solides gestions de concurrence)
    </p>
    <p>
      La lisibilité : séparer les informations dans des tables avec des noms
      explicites aide les développeurs à comprendre ce qu'ils font <br />
      Si il n'est pas absurder d'imaginer pouvoir trouver les informations de
      contact dans une table propriétaire, il est en tout cas clair qu'une table
      <i>information_contact</i> sera destinée à ce type d'information
    </p>
    <p></p>
  </section>
</template>
