---
title:
- Agile infrastructure and operations: how infra-gile are you?
author:
- Patrick Debois
translator:
- Winael
email:
- Patrick.Debois@sos.be
---

# Infrastructure et opérations agiles : dans quelle mesure êtes-vous infra-gile ?

## Résumé

_Certains ont décrit Agile et Infrastructure comme étant un oxymore : ils ne s'emboîteraient tout simplement pas. Pendant un an, nous nous sommes concentrés sur l'utilisation de techniques agiles pour gérer trois projets d'infrastructure différents. D'un point de vue infrastructurel unique, nous montrerons que le terme " infrastructure agile " se compose de plusieurs couches._

_Pour être efficace, chaque couche doit être traitée._

## 1. Cas n°1 : Migration de Datacenter

### 1.1. Application parc à ferrailles

Notre premier projet a été la construction d'une nouvelle infrastructure de centre de données. L'environnement de production contenait plusieurs applications inachevées, non prêtes pour de la production. Beaucoup de ces applications avaient été forcées sur l'infrastructure du centre de données : le développement d'une nouvelle application dépassait toujours les délais.

Comme d'habitude dans les grandes entreprises, les équipes développement, de gestion de  l'infrastructure et d'exploitation étaient des groupes distincts.

Les équipes de développement et celle gérant l'infrastructure travailleraient de façon isolée sur un projet et n'intégraient leur travaux respectif que juste avant la date limite politique pour présenter l'application aux opérations. Il ne restait alors plus de temps pour arranger les choses.

Un nouveau centre de données permettrait de nettoyer la situation en migrant les anciennes applications vers un nouvel environnement plus contrôlé.

### 1.2. Une nouvelle infrastructure, un nouvel espoir

Un groupe d'architectes a été chargé de décrire les exigences de ce nouveau centre de données. Ils se sont concentrés sur le nouveau design et ont proposé des améliorations à la fine pointe de la technologie : de nouveaux cadres de développement, de nouveaux serveurs d'applications et une infrastructure évolutive permettant d'acheter de nouvelles machines plus puissantes. Pour la gestion du centre de données, ITIL serait introduit en tant que processus.

Ils n'ouvriraient leur centre de données vers de nouvelles applications qu'une fois que chaque système ou processus complètement détaillé. Le déploiement d'une application ne serait qu'un simple cas d'application des nouvelles lignes directrices.

Ils n'ont pas ressenti le besoin de parler aux différents projets, car leur environnement serait générique à toutes les applications.

Les nouvelles applications devaient aller directement dans le nouveau centre de données. Comme la description du nouveau centre de données prenait plus de temps que prévu, les nouveaux projets ont été retardés au lieu de progresser. Le président de l'entreprise est devenu nerveux et l'a exprimé ainsi : "Je m'en fiche si ce n'est pas fini, mais il doit y avoir quelque chose dessus et tu pourras continuer à améliorer les choses après." Un petit groupe de travail ferait donc avancer les choses.

### 1.3 Changement d'état d'esprit

En étudiant les critères de test des applications, le groupe de travail a découvert plusieurs concepts inspirés par l'agilité, comme le développement piloté par les tests et Scrum. La majeure partie de la documentation portait sur le processus d'élaboration, mais ils ne pouvaient contrôler que le processus d'infrastructure.

Scrum en tant que méthodologie de projet n'était pas nécessairement liée au développement. Il semblait y avoir une parfaite adéquation entre l'idée de conception itérative et la demande du président : A chaque sprint, vous auriez une nouvelle version qui fonctionnerait et qui serait constamment améliorée.

Ils allaient expérimenter pour voir que les concepts agiles fonctionnaient effectivement bien pour les projets d'infrastructure.

### 1.4. Applications en tant que Clients

Au lieu de construire un centre de données générique, le groupe de travail a contacté chaque chef de projet pour participer aux réunions du projet. Chaque application était considérée comme un client pour le centre de données. De cette façon, ils ont commencé à compiler leur backlog, en leur assignant différentes priorités. Cette interaction leur a également permis de mieux comprendre les besoins de leurs projets, qui étaient leurs clients. Les projets ont pris conscience de la nature partagée de l'infrastructure et ont mieux compris les problèmes d'ordonnancement. Le groupe de travail a également pu mettre en évidence plusieurs exigences non fonctionnelles telles que la sécurité, la performance, la gestion des logs, la surveillance qui n'avaient pas été prises en compte. Une première liste a été dressée et les priorités pour les deux prochaines semaines ont été discutées : le contenu de leur premier sprint.

### 1.5. Un environnement de travail minimal

L'objectif principal du groupe de travail était de commencer à construire un environnement temporaire qui pourrait accueillir les nouvelles applications, jusqu'à ce que le nouveau centre de données soit prêt. Un environnement de travail minimal exigeait généralement plusieurs semaines car de nombreux groupes différents devaient interagir : serveurs, mise en réseau, surveillance, stockage et nouveau matériel étaient encore en attente.

Un à un, ils ont commencé à surmonter leurs dépendances. Les serveurs DNS manquants étaient compensés par l'utilisation de fichiers hôtes. Les serveurs faisaient le routage au lieu des routeurs. L'utilisation du balisage VLAN sur les interfaces permettait de surmonter le manque de ports réseau. L'équilibrage de charge et la terminaison SSL étaient effectués dans le logiciel plutôt que dans le matériel. Des disques internes étaient utilisés pour les données afin de constituer les matrices de stockage manquantes. Ces solutions n'étaient pas définitives et devaient être remplacées lorsque la solution définitive serait disponible. Mais au moins, c'était un environnement de travail.

### 1.6. Déployer souvent

La livraison du premier sprint devait être testée par un déploiement réussi de la première application. Encore une fois, c'était un désastre : plusieurs fichiers de configuration manquaient, les développeurs travaillaient sur une autre version de la base de données, et il n'y avait pas de suivi. Il y avait déjà eu des discussions semblables dans le passé. La différence, c'est que maintenant qu'ils avaient encore du temps avant la date limite, ils pouvaient réessayer de déployer. Dans le même temps, l'infrastructure fût également améliorée en parallèle. Après trois déploiements tests, les avantages étaient clairs : beaucoup moins de problèmes d'intégration. L'application a pu être mise en service et même pendant la production, et ce processus d'amélioration s'est poursuivi. Chaque version améliorait à la fois le logiciel et l'infrastructure.

### 1.7. Contrats de Niveaux de Service

L'approche progressive a eu un effet secondaire intéressant : dans le passé, lorsqu'une application était mise en service, un Contrat de niveau de service était négocié entre le client et son partenaire externe. Comme il s'agissait du document qui décrivait le moment où les pénalités devaient être payées, ce document a souvent suscité d'énormes discussions. Avec la nouvelle approche progressive, quand l'application était-elle terminée ? Les gestionnaires des Contrats de niveau de service n'étaient pas dans la boucle de la discussion. Même avec des améliorations significatives, les opérations ne signeraient pas l'acceptation, car on ne savait pas quand l'application ou l'infrastructure était terminée.

## 2. Cas n°2 : Reprise après sinistre

### 2.1. Dette technique

Notre cas suivant était axé sur la reprise après sinistre : une entreprise avait connu plusieurs pannes et de l'argent avait été perdu. Les mises à jour des infrastructures ont été reportées parce que l'impact n'était pas prévisible sur un environnement incontrôlé, d'où une dette technique importante. Là encore, l'idée était qu'une migration vers une nouvelle plate-forme matérielle résoudrait ces problèmes. Le responsable avait déjà eu de bonnes expériences avec Scrum utilisé par un groupe de développement et avait décidé que le groupe en charge de l'infrastructure l'utiliserait.

### 2.2. Groupe contre équipe

Le groupe se composait de cinq personnes dont chacune avait son expertise spécifique : réseau/sécurité, bureautique, serveurs et stockage, applications et middleware. Chaque membre a dressé une liste des éléments qu'il jugeait nécessaires pour améliorer la situation. Ils considéreraient cette liste comme leur backlog de produit. Leur manager a mis des priorités sur la liste et le premier sprint a été défini par la question suivante : que pouvez-vous finir en deux semaines ? L'estimation de groupe ne fonctionnait pas bien, car bien souvent, il n'y avait qu'une seule personne qui pouvait dire quelque chose sur une tâche donnée.

### 2.3. Tâches et tickets : un cocktail mortel

Au cours du premier sprint, il est apparu clairement que les incidents l'emportaient souvent sur la planification d'un membre de l'équipe. Pour chaque incident, il y avait un ticket enregistré. Une nouvelle tâche a été créée sur le Scrum-board appelée 'Héritage'. Cela permettrait d'héberger toutes les tâches émergentes en cas d'incident. A la fin du premier sprint, le tableau était rempli de ces petites tâches. L'analyse de la liste des tickets a devait permettre de mieux comprendre combien de temps devait être alloué aux incidents et combien de temps il restait pour l'amélioration du projet.

La liste des tickets s'est avérée être un mélange de demandes de service, de problèmes et d'incidents. Au lieu de planifier ces demandes, on les a simplement ajoutées à la liste des incidents. Les projets en ont profité pour introduire de nouveaux travaux ou des changements de dernière minute sous la forme d'incidents, difficiles à refuser. Les membres de l'équipe en profitaient aussi, ils reliaient leurs propres intérêts à l'incident, d'une certaine façon, pour travailler sur des tâches plus intéressantes.

### 2.4. Règles de priorité

Pour avoir une meilleure vue d'ensemble, les tickets ont été revus et répartis en incident, amélioration et projet. Afin de permettre au groupe de se concentrer, le responsable a décidé que l'ordre approprié serait d'abord les incidents, ensuite la liste des améliorations et enfin l'aide aux projets. Le raisonnement consistait à dire qu'une fois la liste des améliorations terminée, il serait plus facile d'aider les projets.

Lorsque les responsables de projet ont demandé où en était leur ticket, il leur a été répondu qu'ils n'étaient pas sur la liste pendant les deux semaines suivantes. Certains ont commencé à demander des exceptions au responsable, qui a souvent dû se conformer à leurs demandes. D'autres ont changé de tactique et se sont présentés en personne à l'équipe chargée de l'infrastructure et ont exercé des pressions sociales. Sur le Scrum Board, les priorités changeaient chaque jour, le projet qui criait le plus fort obtenait alors la première priorité et le focus était perdu.

### 2.5. Essayer de plaire à plus de maîtres

Au lieu de décider des priorités lors de la réunion de Sprint-planning suivante, le responsable a invité tous les chefs de projet. Lorsqu'ils ont vu l'énorme backlog, ils ont commencé à comprendre pourquoi ils constataient ces retards. Ils n'avaient connaissance que de leur propre projet et ne n'imaginaient pas la liste globale. Dans le groupe Infrastructures, tout s'est mis en place.

Le product backlog a été réorganisé de manière à satisfaire tous les projets. Au final, la présence d'un directeur a été nécessaire, car tous les projets, y compris le projet d'amélioration de l'infrastructure, se considéraient comme le projet le plus important. Désormais, l'équipe avait un seul propriétaire de produit au lieu de plusieurs.

Afin d'augmenter les ressources, l'équipe en charge de l'infrastructure a été renforcée avec des ressources de l'équipe de test et de l'équipe middleware. Ces ressources supplémentaires avaient déjà des affinités avec l'infrastructure et ont été utilisées pour travailler en mode projet. Les tâches du projet ont été transférées aux nouveaux membres de l'équipe, les incidents et les améliorations sont restés du ressort des membres de l'équipe initiale.

### 2.6. Nous n'avons pas besoin d'un autre cimetière

Au cours des sprints suivants, le travail d'amélioration n'a pas progressé, car ces membres de l'équipe étaient encore continuellement écrasés par des incidents. Les tâches liées au projet sont devenues dépendantes du nouvel environnement qui ne serait commandé que si la conception était complètement terminée et  tous les détails décrits.

En revanche, les personnes orientées projet ont utilisé la virtualisation sur des serveurs disposant d'une capacité inutilisée pour accueillir les nouvelles applications. A chaque sprint, ils amélioraient un petit environnement temporaire basé sur les nouveaux besoins de l'application.

### 2.7. Agile contre Cascade

La plupart des projets utilisaient Prince2 comme style de gestion. Un projet a utilisait Scrum pour son développement. Le projet géré en Scrum ne demandait que ce qui changerait lors du prochain sprint et intégrait les changements dans son product backlog.

Les chefs de projet plus traditionnels se sont plaints de la nouvelle méthode de travail incrémentielle : leurs développeurs devaient constamment adapter leur code en fonction de l'évolution de l'environnement, ces changements n'étant pas prévus et entraînant des travaux supplémentaires. Ils n'avaient pas de moyens faciles de modifier leur code et ne pratiquaient pas le développement piloté par des tests. Ils ont pris l'évolution constante de l'environnement comme un signe d'incompétence, même lorsqu'il s'améliorait avec le temps.

### 2.8. Tout le monde ne voit pas le tableau d'ensemble

Les opérationnels étaient encore présents dans le Scrum quotidien mais étaient de moins en moins intéressés : leur journée consistait à fermer des incidents et non pas à aider les projets. Ils n'étaient pas d'accord pour dire que les priorités du projet étaient leurs priorités : ils installeraient de nouveaux serveurs/versions même si ce n'était pas la priorité globale. Ils considéraient que leur travail consistait à améliorer l'infrastructure et non pas à créer de la valeur commerciale par de nouveaux projets. Pourquoi les améliorations ne figurent-elles jamais en tête de liste ?

Cette discussion permanente sur les priorités augmentait la tension entre le responsable de l'infrastructure/de l'exploitation et le responsable général. Les gens ont commencé à vraiment souffrir de leur petite guerre. Pire encore, la confrontation est devenue personnelle et le responsable opérationnel a démissionné.

Le responsable général a de nouveau introduit le jeu des rôles et responsabilités : chacun dans sa zone et laissez-moi contrôler le flux de qui fait quoi. Et mis fin à cette culture de communication. Toute l'expérience a été enterrée en un mois. Finalement, ils ont mis en place une nouvelle infrastructure qui, dans les premières semaines, présentait les mêmes instabilités que l'ancienne plate-forme. Inutile de faire un projet de reprise après sinistre si votre problème se situe en dehors du problème technique.

## 3. Cas n°3 : Mise à niveau d'un serveur d'application

### 3.1. Logiciels partagés dans le cadre de l'infrastructure

Dans notre troisième cas, une entreprise qui travaillait depuis plusieurs années en mode projet Scrum migrait vers une nouvelle version de son serveur d'application. Les développeurs avaient identifié cette solution aux problèmes de performance. Une tâche aussi simple que d'exécuter un assistant avec suivant, suivant, suivant prenait beaucoup plus de temps que prévu : le système de surveillance devait être adapté, toute la sécurité devait être testée, et qu'en était-il de la haute disponibilité ? De ce simple serveur d'application dépendait un grand nombre de composants d'infrastructure partagés. Une petite évaluation a été entreprise pour évaluer les améliorations à apporter.

### 3.2. Production et test : similarité ?

La mise à jour dans l'environnement de développement et de test avait été facile. Celle de l'environnement de production était beaucoup plus complexe avec des outils de clustering et de gestion qui n'ont été installés que par la suite dans l'environnement de test. L'infrastructure avait été mise en place dès les premières étapes du processus agile au sein de l'entreprise. Elle avait été conçue comme une infrastructure générique et sans connaître les applications réelles et avait souffert d'une féaturite : elle comprenait toutes les cloches et tous les sifflets qui pouvaient être inclus car au moment de la construction les exigences n'étaient pas claires pour le groupe gérant l'infrastructure, les deux parties travaillaient dans deux groupes différents.

### 3.3 Toute la pile, s'il vous plaît.

Une autre différence résidait dans le fait que le test et le développement se déroulaient dans des environnements virtuels, utilisant des configurations légères du serveur d'application pour pallier le manque de ressources machine. Ils utilisaient une version plus récente du système d'exploitation. Mettre à niveau le système d'exploitation en même temps que le serveur d'application se justifiait. La mise à niveau du système d'exploitation impliquait de nouveaux agents de surveillance et de sauvegarde. Mais au moins désormais les mêmes pilotes JVM, JDBC et la même version de base de données pouvaient être utilisés.

En étendant les scripts de déploiement existants, l'installation complète d'une nouvelle machine virtuelle comprenant le système d'exploitation, la JVM, le serveur d'application, les pilotes JDBC, et l'application pouvait être reconstituée. Cela pouvait permettrait d'inclure des correctifs à chaque niveau et de les tester à chaque itération. L'intégration des correctifs permettrait d'éviter les surprises de production. Lors d'un entretien sur la façon d'améliorer les choses, tout le monde s'est souvenu de l'itération avec les sept correctifs et ne voulait pas que ce cauchemar ne recommençe.

### 3.4. Suivi des changements et de leur impact

Le problème qui se pose avec ces scripts d'intégration c'est qu'ils doivent être maintenus, si l'infrastructure est dédiée au projet, cela ne pose pas trop de problèmes. Dans un environnement de production, le réseau, le stockage, la surveillance et la sécurité sont souvent partagés. Et cela signifie que tous les projets doivent prendre note et étudier l'impact de ces changements. Cela a souvent posé des problèmes, des modifications ont été apportées à la production en raison d'autres projets et la prédiction de l'environnement de test ne s'est pas avérée utile.

Un architecte de production pourrait suivre ces changements dans le cadre de sa description de poste. Le responsable opérationnel s'est montré très intéressé dans la mesure où il pourrait s'agir en quelque sorte d'un garde-fou. Le groupe de projet agile comprenait très bien l'idée, mais avait déjà depuis longtemps abandonné l'idée de ne faire appel qu'à l'architecte. Quelques discussions plus tard, il est apparu clairement que le candidat à ce poste devait être neutre à la fois pour les opérations et pour le projet et qu'il ne pouvait le faire qu'en travaillant qu'au côté du responsable opérationnel et du chef de projet. Personne dans le groupe existant n'était assez neutre. Au lieu d'affecter la responsabilité à une seule personne, la tâche a été assignée au groupe d'infrastructure au sein du projet en tant qu'intermédiaire.

### 3.5. 80% projet, 20% piège opérationnel

Deux personnes chargées de l'infrastructure ont été affectées 80 % au projet et 20 % à d'autres travaux. Ils ont effectué le travail d'infrastructure pour assister les autres membres de l'équipe mais n'ont pas participé aux mêlées quotidiennes ou n'ont pas travaillé sur une partie de ce backlog, car leur travail semblait simplement tomber dans la catégorie des diversités. En réalité, ils se situaient quelque part entre le mode projet et le mode opérationnel, étant dirigés par deux responsables différents, qui avaient toujours l'impression de devoir décider des priorités nécessaires. Ils étaient également désolés pour le projet s'ils ne pouvaient pas tenir leurs promesses. L'équipe sentait qu'ils n'étaient pas assez engagés parfois. Ils ont donc travaillé dur pour essayer de plaire aux deux groupes.

Lors des discussions du backlog produit, leur travail n'était pas répertorié car il ne créait pas de valeur commerciale directe. Les clients exprimaient surtout leur désir de nouvelles fonctionnalités et non de travaux d'infrastructure. Le sprint-planing suivant, leur travaux allaient faire l'objet d'un backlog séparé : le groupe applications/développeurs deviendrait leurs clients pour leurs récits utilisateur. Sur ce même backlog, ils pouvaient suggérer des tâches pour améliorer l'infrastructure en rendant leur travail visible pour le client. Ces tâches comprendraient une estimation de la valeur qui serait perdue si les choses n'étaient pas améliorées.

### 3.6. Conception et estimations jointes

Pendant la migration, les développeurs avaient fait la majeure partie de la conception initiale de la migration et, bien qu'ils étaient à l'aise avec les nouvelles technologies, le groupe des infrastructures fini par arriver. Ils ont dû se familiariser avec les nouvelles versions sous la pression des délais et des engagements pris par le groupe de développement du projet. Bien que ces délais aient constitué un engagement de groupe, les personnes chargées de l'infrastructure n'avaient pas été consultées au moment de l'estimation et de la conception. Une fois que la liste des tâches s'est étoffée, les développeurs ont commencé à voir qu'il y en avait bien plus que ce à quoi ils pouvaient penser. Ce n'était pas pour gagner du temps, mais simplement parce qu'ils n'étaient pas conscients de toutes ces dépendances. Lors de la réunion de conception suivante, les personnes chargées de l'infrastructure ont été conviée afin de connaître leur point de vue. Tout le monde n'a pas une vue d'ensemble de tout, mais un effort de groupe devait permettre d'y remédier.

### 3.7. C'est qui le patron ?

Après avoir rendu leur travail visible, il est devenu évident qu'ils devenaient cruciaux pour un bon flux de production. Le responsable de l'exploitation craignait de perdre les théoriques 20% supplémentaires, il était difficile de trouver des personnes ayant une affinité à la fois pour l'infrastructure et les applications. Les gens de l'infrastructure voyaient souvent les applications comme une nuisance, ce qui est étrange dans la mesure où les applications d'apportent de la valeur à l'entreprise. Mais les changements apportés par les applications et les projets augmentent l'instabilité de l'environnement. La controverse entre les deux managers s'est intensifiée et les priorités ont dû être abordées au niveau global de l'entreprise et non au niveau local d'un projet ou des opérations.

### 3.8. Le flux est plus important que les backlogs.

Tout en résolvant tous les problèmes au niveau technique et au niveau du projet, l'entreprise était toujours aux prises avec des conflits liés aux opérations et au projet. Une fois franchi cet obstacle, ils ont pu atteindre un nouveau niveau d'infrastructure agile. Au lieu de se concentrer sur les optimisations locales, ils étudient maintenant de nouveaux concepts comme le Kanban afin de faire passer le flux à travers toute l'entreprise. Cela devrait leur permettrait de mener leurs projets et leurs opérations à un rythme qui fonctionne.

## 4. Tendances observés

Dans les trois cas, nous avons découvert plusieurs tendances. Nous avons regroupé ces tendances en trois catégories : Technique, Projet et Opérations. Les aspects techniques ont trait au matériel et aux logiciels utilisés dans l'environnement.

Le projet concerne le cheminement qui introduit les changements dans l'environnement. L'exploitation est le fait de maintenir l'environnement en bon état de fonctionnement. Nous considérons ceci comme les trois couches auxquelles se rapporte l'infrastructure Agile.

### 4.1 Sur le plan technique

- Une migration " technique " est considérée comme la solution à des années de problèmes.
- Les migrations techniques sont des facteurs facilitant le passage à l'Agilité et utilisent souvent des techniques de virtualisation et d'automatisation, convertissant l'infrastructure statique en infrastructure agile.
- L'utilisation de ces techniques nécessite l'acquisition de nouvelles compétences techniques.
- La boîte à outils de l'infrastructure n'est pas encore aussi étendue que la boîte à outils du développeur pour la refactorisation, il est donc important d'avoir quelques directives pour éviter beaucoup de refactoring de l'architecture de base.
- Remplacer tout le matériel ne résoudra pas le problème. Il créera un nouvel environnement " incontrôlé " si seule la plate-forme est remplacée.
- Les infrastructures non agiles ont tendance à vieillir parce que les changements sont difficiles à exécuter dans ces environnements. Cela peut être considéré comme une dette technique.
- Un petit environnement peut créer suffisamment d'espace pour qu'un processus de conversion puisse avoir lieu. Il y a souvent assez de matériel 'perdu' disponible pour en faire jaillir un nouvel usage.
- Les serveurs de builds en continu, les serveurs de test, les outils de couverture de code et les serveurs de versioning font également partie de l'infrastructure et l'équipe en charge de l'infrastructure peut également s'en charger. Cela leur permettra de développer des affinités avec les environnements des développeurs.
- Même les scripts utilisés par les gens de l'infrastructure peuvent tirer avantage d'un système de gestion des versions comme CVS.

### 4.2 Sur le plan projet

- Les compétences techniques doivent être complétées par une mentalité agile. Tout comme pour les aspects techniques, pour accélérer les choses, des chefs de projet agiles et expérimentés pilotent le changement.
- Le développement et l'infrastructure doivent être considérés comme un tout et non comme deux projets distincts. Cela est particulièrement difficile dans les grandes entreprises où les deux appartiennent à des entités différentes.
- La conception des développements doit inclure la conception de l'infrastructure et de l'exploitation pour faciliter l'intégration.
- Dans le cas contraire, chaque projet créera un optimum local, mais l'optimum de l'entreprise ne sera jamais atteint ; les accords de niveau de service (SLA) expriment des besoins qui doivent être inclus dans le backlog.
- Chaque changement nécessitera éventuellement l'adhésion de la direction pour qu'il puisse persister.

### 4.3. Sur le plan des opérations

- Une fois le projet terminé, le groupe opérationnel bénéficiera de l'environnement de test et d'intégration : Contrairement au mode projet, c'est maintenant l'environnement qui change en raison des correctifs de sécurité ou des nouvelles versions.
- Les personnes chargées de l'infrastructure ont souvent des liens étroits avec la partie opérationnelle de l'entreprise.
- Les opérations ne fonctionnent pas en mode projet et si vous incluez du personnel ou des dépendances, votre projet sera imprévisible. Les estimations ne fonctionneront pas, car les incidents sont imprévisibles.
- Les gens entre le projet et les opérations perdront leur concentration et, dans le pire des cas, pourront s'en servir pour ne jamais avoir à terminer leurs tâches.
- Il n'est souvent pas possible d'embaucher du personnel supplémentaire dans le groupe opérationnel car ils sont perçus comme n'apportant aucune valeur ajoutée à l'entreprise. Lorsqu'ils font partie de votre processus de déploiement, leur disponibilité est cruciale.
- Les projets peuvent être hyperproductifs pour le groupe des opérations : ils tentent d'optimiser leur processus de production, mais ils ne considèrent souvent pas le flux du résultat au travers de totalité de l'entreprise et les opérations en deviennent le goulet d'étranglement. Les opérations sont généralement le lieu où de multiples projets se rassemblent et chaque projet pourrait ne pas avoir de vision sur d'autres projets. Il est crucial de le dire clairement et il est difficile de parvenir à un consensus entre les responsables de projet sur les priorités dans la perspective uniquement d'un support .
- Les opérations savent très bien que les changements introduisent des incidents. Par conséquent, ils pensent que leur rôle est de minimiser les changements dans l'environnement de production. Ils servent toujours le même client que le projet. Par conséquent, le projet doit avoir une vue d'ensemble des exigences que le client impose aux opérations.
- Changer le processus de votre projet aura un impact sur la façon dont les SLA sont discutés.

### 4.4. Conclusion

L'introduction réussie de l'infrastructure Agile consiste à traiter à la fois les aspects techniques, de projet et d'exploitation. La partie technique est la plus facile, les outils deviennent matures et intégrés et c'est ce que les informaticiens comprennent le plus facilement. Sur cette base technique, les travaux d'infrastructure peuvent maintenant être intégrés au projet. Le plus difficile, c'est de s'intégrer au caractère imprévisible des activités des opérations, de dépasser les limites du projet et de partager les ressources opérationnelles avec d'autres projets.

## 5. Lectures complémentaires

[1] Pritchett, Dan, _Operational Manageability lessons learned from eBay_, 20 September 2007,
http://www.infoq.com/news/2007/09/operational-mangeability
[2] Hendrickson, Elisabeth, _You’re Kidding. It does WHAT in Production !?!_, 22 May 2007,
http://video.google.com/videoplay?docid=627761504105495
8810
[3] Wilson, Scot, _Agile Operations_, 27 September 2007,
http://www.indigomoonsystems.com/status/status.php?/archives/259-Agile-operations.html
[4] Anderson, David J., _Operations Review_, 20 September
2007,
http://www.agilemanagement.net/Articles/Weblog/OperationsReview-2.html
[5] Nicolette, Dave, _Managing non-functional requirements and enterprise standards_, 30 December 2007
http://dnicolet1.tripod.com/agile/index.blog?entry_id=1776642
[6]Berteig, Mishkin, _Agile Infrastructure Projects_, 28 May 2005
http://www.agileadvice.com/2005/09/28/agilemanagement/agile-infrastructure-projects-lessons-learned/
[7] Gibbs, Ed, _Agile With Infrastructure Projects_ , 14 January 2008,
http://edgibbs.com/2008/01/14/agile-with-infrastructure-projects
http://times.usefulinc.com/2006/06/17-agile-infrastructure ,
[8] Coon, Mike, _Agile Infrastructure_, 10 November 2007,
http://blog.mikecoon.net/2007/11/10/agile-infrastructure.aspx
[9] Agile 2006 Conference, _Agile Infrastructure_, 2006,
http://agile2006.stikipad.com/public/show/AgileInfrastructure
[10] Terry, Hamilton, _Agile for Infrastructure_, 2007,
https://www-927.ibm.com/ibm/cas/archives/2007/workshops/workshop22.shtml
[11] Schiel, Jim, _Scrum and an ‘operational’ team, Scrumdevelopment mailing-list_, 6 March 2008,
http://groups.yahoo.com/group/scrumdevelopment/message/27881
[12] Debois, Patrick, _Agile Infrastructure Operations_,
http://www.jedi.be/agille-infrastructure
