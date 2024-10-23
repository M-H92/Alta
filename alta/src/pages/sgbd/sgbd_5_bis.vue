<template>
  <section>
    <h2>One to Many</h2>
    <p>
      La cardinalité <strong> One to Many </strong> permet, comme son nom
      l'indique (Un vers Plusieurs en français) de lier un record à plusieurs
      records <br />
      Des exemples d'utilisations pourraient être :
    </p>
    <p>
      <strong> Sélection parmis une liste </strong> <br />
      Un record donné fait partie dispose d'une information qui fait partie
      d'une liste qu'il doit respecter (comparable à une énumération dans vos
      cours de C)<br />
      Un chat pourrait avoir une race parmis une liste définie (maine coon,
      persan, bleu russe, british shorthair...) <br />
      Ceci permet d'éviter d'encoder des valeurs non définies et, par
      conséquent, des erreurs d'exécution dans votre code. <br />
      Par exemple, si vous tentez de traiter un document pouvant être une
      <i>FACTURE</i> ou une <i>NOTE_DE_CREDIT</i>, une comparaison avec la
      valeur <i>note_credit</i> pourrait faire planter l'application
    </p>
    <p>
      <strong> Disposer de valeurs de références </strong> <br />
      Dans notre base de données, une race dispose d'un poids idéal et on peut
      ainsi calculer la différence entre le poids réel et le poids idéal de
      notre animal. <br />
      Il s'agit du même cas d'utilisation que la sélection dans une liste, mais
      avec l'ajout de plus de valeurs
    </p>
    <p>
      <strong>
        Créer un critère commun pour une récupération de données
      </strong>
      <br />
      Je pourrais par exemple lier une table facture à une table client avec une
      relation One to Many (un client et many factures) <br />
      Ainsi, je peux récupérer les factures sur base du client particulier
    </p>
    <h2>Many to Many</h2>
    <p>
      La cardinalité <strong> Many to Many </strong> (en français, plusieurs
      vers plusieurs) permet de lier plusieurs records à plusieurs records.
    </p>
    <p>
      Nous avons déjà un exemple avec nos rappels de vaccins : <br />
      Un chat peut avoir plusieurs vaccins <br />
      Un vaccin peut être appliqué à plusieurs chats
    </p>
    <p>
      Très vite, on se rend compte qu'on ne peut pas utiliser le même type de
      mise en relation que pour les One to Many <br />
      Si je mets une FK depuis le chat vers le vaccin, un chat ne pourra avoir
      qu'un unique vaccin <br />
      Si je mets une FK depuis un vaccin vers un chat, le vaccin se retrouve lié
      à ce chat en particulier <br />
      Cette cardinalité requiert une structure particulière : une
      <strong>join table</strong> (table de liaison ou intermédiaire) <br />
      Cette table sera définie par au moins deux FK. <br />
    </p>
    <h2>One to One</h2>
  </section>
</template>
