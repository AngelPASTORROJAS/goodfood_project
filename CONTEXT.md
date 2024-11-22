# Good Food 3.0

## L'entreprise Good Food
### Historique et présentation
Good Food a été créée en 1992. Elle est la fusion de 4 entreprises de restauration ayant principalement pour clientèle des employés du secteur tertiaire. La fusion de ces 4 entités a permis mécaniquement d’augmenter les volumes d’achats et donc de négocier les prix, tout en rationalisant l’offre qui comprend :
- Des prestations de restauration conventionnelle
- De la vente à emporter
- Des prestations de livraison (commande par téléphone)
La marque Good Food était créée. 
Diverses opérations d’acquisition d’établissements concurrents ont tout naturellement abouti à la création d’une franchise en 1995.
Désormais Good Food est devenu une franchise commerciale regroupant des franchisés.
### Franchises et réseaux de franchisés
Le réseau de franchisés s’est développé et a été rejoint par d’autres restaurants mais également d’autres groupements similaires déjà existants. Le « poids » de ces groupements nouvellement arrivé n’a pas été sans conséquences sur la gouvernance de la franchise et nombre de restaurants ont demandé des aménagements spécifiques (élaboration de plats particuliers, prix et remises promotionnelles spécifiques, fournisseurs spécifiques)
### Implantations géographiques
Les établissements d’origine se situent en banlieue parisienne.
La croissance du groupe lui permet maintenant d’être présent dans les 20 plus grandes métropoles françaises, en Belgique et au Luxembourg.
### Quelques données du groupe
- 150 restaurants sur la France, la Belgique et le Luxembourg
- 1 millier de collaborateurs
- 200 recettes proposées sur l’ensemble des restaurants
- 1 million de repas livrés sur l’exercice 2023
- La vente en ligne qui représente 80% du CA
## Organisation de l'entreprise
### Services internes
Le siège de Good Food, outre la direction et la présidence du groupe, comprend les services
suivants :
- Un service comptabilité qui a en charge de récupérer les données relatives à la vente en ligne des restaurants du groupe et des établissements franchisés. Elle a aussi la charge de la comptabilité relative aux paiement TPE des restaurants rachetés par le siège Good Food Elle n’a pas la charge des paiements physiques des groupements ayant rejoint le groupe  
- Un service communication et community management qui centralise les remarques et mécontentement des utilisateurs par téléphone ou email  
- Un service informatique composé de 4 personnes
Cela représente un peu plus de 30 personnes.
### Sous traitance (cas du service informatique)
Dès la création du groupe, le choix a été fait de sous-traiter la plupart des opérations. Le service informatique gère essentiellement le support de niveau 1. Les intervenants extérieurs se répartissent de la façon suivante :
- La société PWI est en charge de l’hébergement de l’application de commande en ligne et en assure la supervision. Les serveurs hébergeant cette application sont situés dans le « mini » datacenter de la société
- L’agence WIM (Web & Internet Makers) qui a développé l’application
- TP System, qui déploie et gère les terminaux de paiement dans tous les restaurants de la franchise. Elle a la charge d’intégrer les TPE des restaurants avec le système bancaire BNB
- BNB, banque de l’entreprise, qui fournit également une solution de paiement virtuelle pour les achats en ligne. C’est la banque principale pour l’ensemble des franchisés
## Le projet
### Etat des lieux
Dans le cadre de sa croissance, Good Food a mis en place une première solution applicative de commande en ligne sur son site en 1998 développée en Java.
Pour faire face au changement de mode de consommation des clients qui s’orientaient de plus en plus vers des solutions e-commerce, l’application a été refondue en 2005 et développé en ASP.NET avec le langage C#.
Après plusieurs années de production, la plate-forme pose des problèmes :
- Solution tournant sur Windows Server 2008 R2 dont le support n’est plus assuré par Microsoft  
- Des choix applicatifs qui empêchent toute évolution (librairies obsolètes, codage maladroit, patchs sur patchs)
- Des performances qui plafonnent malgré les quelques optimisations mises en œuvre par l’hébergeur
- L’absence de solution mobile
- Le code n’est pas documenté et a subi des modifications au gré des demandes des franchisés
- De nombreux bugs persistent pour les clients (impossibilité d’utiliser des codes de réduction, temps de réponse des pages) et pour les utilisateurs
### Audit prestataire en développement web
Comme mentionné précédemment, les habitudes des consommateurs ont évolué et le site n’offre plus l’expérience que les clients sont en droit d’exiger d’une enseigne comme Good Food, surtout dans un marché qui devient de plus en plus concurrentiel.
La direction a décidé de faire auditer le site et l’infrastructure par la société DIW (Do It Web), spécialiste en développement web et mobile hybride.
Voici leurs préconisations :
- L’application doit être intégralement refondue, le code en l’état n’est plus maintenable. La seule migration vers une version plus récente du framework .NET n’est pas une solution pérenne.
- Le contexte ayant évolué, il est recommandé d’utiliser des technologies open source en lieu et place des solutions Microsoft.
- Proposer aux clients une application mobile pour effectuer leurs commandes et gérer leur compte. Il faudra prendre en compte l’accessibilité.
- Refondre l’infrastructure d’hébergement pour assurer une disponibilité de service sans faille lors des pics de commandes
- Développer un service pour les franchises et les groupements de franchises pour qu’ils puissent gérer leurs commandes, leurs préparations, leurs fournisseurs et leurs livraisons
- Envisager l’intégration d’un système d’aide à la décision (optionnel)
Note : les préconisations peuvent être remises en cause si cela est justifié
### Exigences de l'entreprise pour refonte de l'application de commande en ligne
Good Food a également fait part de ses exigences pour la refonte de cette application :
- La totalité des données doit être conservée et récupérée dans la nouvelle base
- La migration des données vers la nouvelle solution devra se faire sans aucun impact sur la production
- Le code devra être documenté
- Cette évolution de l’application sera concomitante avec l’adoption d’un nouveau système
de caisse dont le déploiement est assuré par le fournisseur de caisse lui-même
- La nouvelle application devra être accessible depuis d’autres solutions (comptabilité, applications spécifiques de la logistique, etc.)
- L'application devra être bien évidemment conforme au cahier des charges fonctionnel
- La société DYW aura la charge de la conception graphique de la nouvelle solution Good Food et du développement de l’application mobile
- La nouvelle solution doit être compatible avec l’engagement de développement durable dans laquelle Good Food s’est engagée
### Containtes et contexte de l'entreprise
l n’y a pour l’instant aucune compétence en développement dans l’équipe informatique de l’entreprise Good Food
- L’ancien prestataire qui a développé l’application en .NET fait de l’obstruction et ne distille que partiellement ses informations (lesquelles sont incomplètes, l’équipe ayant développé la solution ne faisant plus partie des effectifs)
- Le prestataire fournissant les solutions de paiement dans les restaurants met 2 à 4 semaines pour répondre à une demande d’informations
- Les demandes remontées par les franchisés sont régulièrement en contradiction avec les demandes définies dans le cahier des charges établi par le service informatique
- Consciente des enjeux de la transformation digitale, Good Food désire refondre son service informatique pour créer un vrai pôle informatique afin de reprendre la main sur la maitrise de son SI. Ce nouveau pôle aura la charge du développement de la nouvelle solution.
### A props du SI de l'entreprise Good Food
Vous avez pu récupérer les compléments d’information concernant le SI existant
- Le SI du réseau Good Food est essentiellement construit autour des solutions SaaS de Microsoft
- Les postes des salariés travaillant pour le siège Good Food sont sous Windows 10 ou 11. La suite bureautique Microsoft 365 (Word, Excel, Outlook) est utilisée.
- Tous les franchisés utilisent le serveur de messagerie Microsoft 365.
- Le service comptabilité du groupe utilise le logiciel Sage hébergé sur site sur un serveur situé dans les locaux de la direction. C’est la société PWI qui s’est occupé de l’intégration sur site et de la maintenance de ce serveur.
- Tous les restaurants du réseau sont équipés à minima d’un TPE
- L’ERP Microsoft Dynamics 365 est déployé pour l’ensemble de la franchise. Les modules utilisés sont la gestion financière, la gestion RH, la gestion des clients et la gestion des stocks. La gestion fournisseurs n’est pas prise en charge.
- A noter que de nombreux franchisés utilisent leurs outils internes tels que des tableurs et intègrent pas toujours les informations dans l’ERP surtout au niveau RH et des stocks.
- Le service communication reçoit les réclamations par email depuis l’adresse contact ou du formulaire de contact de l’application de commande en ligne de Good Food, mais parfois aussi par téléphone. Les réclamations et leur suivi sont tracés dans l’ERP.
- L'application Good Food a sa propre base SQL Server 2008
- La synchronisation entre la base Good Food et l’ERP se fait 1 fois par jour à 5h le matin. C'est une application maison C# utilisant WCF développée par l’agence WIM qui est chargée de la synchronisation. Les mises à jour depuis l’application des informations clients et sur les ventes de repas sont envoyées vers l’ERP. L’application de synchronisation WCF est hébergée chez WIM.
- Chaque jour les la banque transfère les transactions bancaires effectuées en ligne de la veille au logiciel de trésorerie de Sage via le protocole EBICS. Les paiements TPE des restaurants du groupe sont aussi transférés. Les paiements TPE des groupements ayant rejoint Good Food ne sont pas inclus.
- Les paiements aux fournisseurs se fait aussi via EBICS. Ils peuvent être effectués par le service comptabilité du siège ou par les services comptabilité des groupements qui ont aussi leurs propres fournisseurs en plus des fournisseurs du groupe.
- Des informations globales sur les ventes et les dépenses sont remontées dans le module finance de Dynamics depuis Sage ou depuis les systèmes de trésoreries des groupements.
- Good Food a aussi un site institutionnel vitrine présentant la franchise développé et mis à jour par des stagiaires. Il est hébergé par PWI. Les technologies sont HTML, CSS, JavaScript, PHP, MySQL Community Edition. Le site est déployé dans un environnement Apache 2.2. Le site est peu maintenu.
Note : Le sujet étant fictif, vous êtes autorisés à ajouter des éléments pour enrichir votre vision du SI tant que ceux-ci ne contredisent pas le sujet.
### Les fonctionnalités de l'application à architecturer
Vous pouvez partir du principe que la nouvelle solution applicative Good Food doit fournira les services / fonctionnalités suivantes :
- La gestion des clients (inscription, gestion du compte, réclamations)
- L’authentification
- La gestion des menus
- La commande de repas (panier en ligne)
- Le paiement
- L’organisation des livraisons (inclue la possibilité d’indiquer l’heure à laquelle il faut livrer)
- Le service des réservations
- Le service franchisé pour créer des promotions, gérer les fournisseurs, etc.
- Eventuellement un service d’analyse des données pour l’aide à la décision
Cette liste n’est là que pour vous orienter sur les composants métiers principaux de la nouvelle solution. Ce n’est pas la peine de rentrer dans le détail des fonctions métiers, ni dans une décomposition trop fine des composants métiers.
Dans cette liste, un service n’est pas synonyme de service technique ou de composant.
Vous avez le droit d’imaginer un découpage différent, alternatif tant que cela est cohérent avec le sujet et ses consignes.