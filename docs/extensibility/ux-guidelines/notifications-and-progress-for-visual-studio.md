---
title: Notifications et progrès pour Visual Studio (en anglais seulement) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f0ef65e9-0f1f-45f4-9f25-6e2398691168
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5f6a7ddd5d1a5a7257617b03098722e1341017b6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699881"
---
# <a name="notifications-and-progress-for-visual-studio"></a>Notifications et progression pour Visual Studio
## <a name="notification-systems"></a><a name="BKMK_NotificationSystems"></a>Systèmes de notification

### <a name="overview"></a>Vue d'ensemble
 Il existe plusieurs façons d’informer l’utilisateur de ce qui se passe dans Visual Studio concernant ses tâches de développement de logiciels.

 Lors de la mise en œuvre de tout type de notification :

- **Maintenez le nombre de notifications au** nombre effectif minimum. Les messages de notification doivent s’appliquer à la majorité des utilisateurs de Visual Studio ou aux utilisateurs d’une zone spécifique de fonctionnalité/fonctionnalité. L’utilisation excessive de notifications peut détourner l’utilisateur ou diminuer la facilité d’utilisation perçue du système.

- **Assurez-vous de présenter des messages clairs et exploitables** que l’utilisateur peut utiliser pour invoquer le contexte approprié pour faire des choix plus complexes et prendre d’autres mesures.

- **Présentez des messages synchrones et asynchrones de façon appropriée.** Les notifications synchrones indiquent que quelque chose nécessite une attention immédiate, par exemple lorsqu’un service Web se bloque ou qu’une exception de code est lancée. L’utilisateur doit être informé de ces situations immédiatement d’une manière qui nécessite leur contribution, comme dans un dialogue modal. Les notifications asynchrones sont des notifications que l’utilisateur doit connaître, mais ne pas être tenu d’agir immédiatement, comme quand une opération de construction se termine ou un déploiement de site Web se termine. Ces messages doivent être plus ambiants et ne pas interrompre le flux de tâches de l’utilisateur.

- **Utilisez les dialogues modaux uniquement lorsque cela est nécessaire pour empêcher l’utilisateur de prendre d’autres mesures** avant de reconnaître le message ou de prendre une décision présentée dans le dialogue.

- **Supprimez les notifications ambiantes lorsqu’elles ne sont plus valides.** N’exigez pas que l’utilisateur rejette une notification s’il a déjà pris des mesures pour résoudre le problème dont il a été informé.

- **Sachez que les notifications peuvent conduire à de fausses corrélations.** Les utilisateurs peuvent croire qu’une ou plusieurs de leurs actions ont déclenché une notification alors qu’en fait il n’y avait pas de relation causale. Soyez clair dans le message de notification sur le contexte, le déclencheur et la source de la notification.

### <a name="choosing-the-right-method"></a>Choisir la bonne méthode
 Utilisez cette table pour vous aider à choisir la bonne méthode pour informer l’utilisateur de votre message.

|Méthode|Utilisation|À ne pas utiliser|
|------------|---------|----------------|
|[Dialogues de messages d’erreur modal](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ModalErrorMessageDialogs)|Utilisez quand une réponse utilisateur est nécessaire avant de procéder.|N’utilisez pas lorsqu’il n’est pas nécessaire de bloquer l’utilisateur et d’interrompre son flux. Évitez d’utiliser des dialogues modaux s’il est possible de montrer le message d’une autre manière moins intrusive.|
|[Barre d’état IDE](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_IDEStatusBar)|Utiliser lorsqu’il y a des informations textuelles ambiantes concernant l’état d’un processus.|Ne pas utiliser seul. Idéal utilisé en conjonction avec un autre mécanisme de rétroaction.|
|[Barre d'informations incorporée](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_EmbeddedInfobar)|Dans une fenêtre d’outil ou une fenêtre de document, utilisez-le pour en informer les progrès, l’état d’erreur, les résultats et/ou les informations exploitables.|N’utilisez pas si les informations ne sont pas pertinentes à l’endroit où l’infobar est placé.<br /><br /> N’utilisez pas à l’extérieur d’une fenêtre de document/outil.|
|[Modifications du curseur de souris](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_MouseCursorChanges)|Peut être utilisé pour informer qu’un processus est en cours. Également utilisé pour informer qu’il ya un changement d’état dans la souris, comme lorsque la traînée / goutte est en cours ou que le curseur de la souris est dans un certain mode, comme le mode de dessin.|Ne pas utiliser pour de courts changements de progression ou si le flottement du curseur est probable (par exemple, lorsqu’il est lié à des parties d’un processus de fonctionnement plus long au lieu de l’ensemble du processus).|
|[Indicateurs de progression](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_NotSysProgressIndicators)|Utilisez lorsque vous devez signaler les progrès (déterminée ou indéterminée). Il existe une variété de types d’indicateurs de progression et d’utilisation spécifique pour chacun. Voir [indicateurs de progrès](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ProgressIndicators).||
|[Fenêtre de notifications de Visual Studio](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_VSNotificationsToolWindow)|La fenêtre Notifications n’est pas publiquement extensible. Cependant, il est utilisé pour communiquer une gamme de messages sur Visual Studio, y compris des problèmes critiques avec votre licence et des notifications d’information des mises à jour de Visual Studio ou à des paquets.|N’utilisez pas pour d’autres types de notifications.|
|[Liste d’erreurs](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ErrorList)|Lorsque le problème se rapporte directement à la solution actuellement ouverte de l’utilisateur ayant un problème (erreur/ avertissement/info), il peut avoir besoin de prendre des mesures sur le code.<br /><br /> Il s’agirait, par exemple , de :<br /><br /> - Compilateur de messages (erreur/avertissement/info)<br /><br /> - Code Analyzer/Diagnostic messages sur le code<br /><br /> - Construire des messages<br /><br /> Peut être approprié pour les questions relatives aux fichiers de projet ou de solution, mais considérez d’abord une indication solution Explorer.|N’utilisez pas pour les éléments qui n’ont aucun rapport avec le code de solution ouvert de l’utilisateur.|
|Notifications de l’éditeur : Ampoule|Utilisez lorsque vous avez un correctif disponible pour remédier à un problème qui existe dans le fichier ouvert.<br /><br /> Notez que Light Bulb doit également être utilisé pour héberger des actions rapides qui sont prises sur le code de l’utilisateur à la demande, tels que les refactorations, mais dans ce cas n’apparaîtra pas "style de notification."|N’utilisez pas pour les éléments qui n’ont aucun rapport avec le fichier ouvert.|
|Notifications de l’éditeur : Squiggles|Utilisez pour alerter l’utilisateur d’un problème avec une durée particulière de son code ouvert (par exemple, un mouvement rouge pour les erreurs).|N’utilisez pas pour les éléments qui ne se rapportent pas à une durée particulière de leur code ouvert.|
|[Barres d’état intégrées](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_EmbeddedStatusBars)|Utiliser pour fournir un statut lié au contenu ou au processus dans le contexte d’une fenêtre d’outil spécifique, d’une fenêtre de document ou d’une fenêtre de dialogue.|N’utilisez pas pour les notifications, processus ou éléments de produits généraux qui n’ont aucun rapport avec le contenu dans la fenêtre spécifique.|
|[Notifications de plateau Windows](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_WindowsTray)|Utiliser pour les notifications de surface pour les processus hors-proc ou les applications complémentaires.|N’utilisez pas pour les notifications qui sont pertinentes pour l’IDE.|
|[Bulles de notification](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_NotificationBubbles)|Utiliser pour informer d’un processus à distance ou changer **en dehors** de l’IDE.|Ne pas utiliser comme un moyen d’aviser l’utilisateur des processus **dans** l’IDE.|

### <a name="notification-methods"></a>Méthodes de notification

#### <a name="modal-error-message-dialogs"></a><a name="BKMK_ModalErrorMessageDialogs"></a>Dialogues de messages d’erreur modal
 Un dialogue de message d’erreur modal est utilisé pour afficher un message d’erreur qui nécessite la confirmation ou l’action de l’utilisateur.

 ![Message d'erreur modal](../../extensibility/ux-guidelines/media/0901-01_modalerrormessage.png "0901-01_ModalErrorMessage")

 **Un message d’erreur modal qui dialogue l’utilisateur d’une chaîne de connexion invalide vers une base de données**

#### <a name="ide-status-bar"></a><a name="BKMK_IDEStatusBar"></a>Barre d’état IDE
 La probabilité que les utilisateurs remarquent le texte de barre d’état est corrélée à leur expérience informatique tout autour et expérience spécifique avec la plate-forme Windows. La clientèle visual Studio a tendance à être expérimentée dans les deux domaines, bien que même les utilisateurs de Windows bien informés puissent manquer des changements dans la barre d’état. Par conséquent, la barre d’état est mieux utilisée à des fins d’information ou comme un indice redondant pour les informations présentées ailleurs. Tout type d’informations critiques que l’utilisateur doit résoudre immédiatement doit être fourni dans un dialogue ou dans la fenêtre de l’outil Notifications.

 La barre d’état Visual Studio est conçue pour permettre l’affichage de plusieurs types d’informations. Il est divisé en régions pour la rétroaction, concepteur, barre de progression, animation, et client.

 La région de rétroaction et la région de concepteur sont toujours visibles. La barre de progression et les régions d’animation sont toujours dynamiques et basées sur le contexte utilisateur. La région de concepteur a une largeur statique déterminée par la longueur de la chaîne qui est tirée d’une ressource d’accompagnement pour le message texte. Cela permet à la localisation de resize la largeur sans nécessiter de modification de code. Pour l’anglais, la largeur de cette chaîne est d’environ 220 pixels. La région de concepteur se comportera normalement et la région de rétroaction absorbera l’espace restant.

 La barre d’état est également colorisée pour ajouter l’intérêt visuel et la valeur fonctionnelle en communiquant divers changements d’état d’IDE tels que lorsque l’IDE est en mode débbug.

 ![Modifications de couleur de la barre d'état IDE](../../extensibility/ux-guidelines/media/0901-02_idestatusbar.png "0901-02_IDEStatusBar")

 **Couleurs de barre d’état IDE**

#### <a name="embedded-infobar"></a><a name="BKMK_EmbeddedInfobar"></a>Infobar intégré
 Une infobar peut être utilisée en haut d’une fenêtre de document ou d’une fenêtre d’outil pour informer l’utilisateur d’un état ou d’une condition. Il peut également offrir des commandes afin que l’utilisateur puisse avoir un moyen d’agir facilement. L’Infobar est un contrôle standard de la coque. Évitez de créer le vôtre, qui agira et semblera incompatible avec les autres dans l’IDE. Consultez [Infobars](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars) pour plus de détails sur la mise en œuvre et les conseils d’utilisation.

 ![Barre d'informations incorporée](../../extensibility/ux-guidelines/media/0901-03_embeddedinfobar.png "0901-03_EmbeddedInfobar")

 **Une infobar intégrée dans une fenêtre de document, alertant l’utilisateur que l’IDE est en mode de débogage historique et l’éditeur ne répondra pas de la même manière qu’il le fait en mode de débogage standard.**

#### <a name="mouse-cursor-changes"></a><a name="BKMK_MouseCursorChanges"></a>Modifications du curseur de souris
 Lors du changement du curseur de souris, utilisez des couleurs qui sont liées au service VSColor et sont déjà associées au curseur. Les modifications de curseur peuvent être utilisées pour indiquer une opération en cours, ainsi que les zones de frappe où l’utilisateur plane au-dessus d’une cible qui peut être traîné, tombé sur, ou utilisé pour sélectionner un objet.

 Utilisez le curseur de souris occupé/attendre uniquement lorsque tout le temps de processeur disponible doit être réservé à une opération, empêchant l’utilisateur d’exprimer toute autre entrée. Dans la plupart des cas avec des applications bien écrites utilisant la multithreading, les moments où les utilisateurs sont empêchés de faire d’autres opérations devraient être rares.

 Gardez à l’esprit que les changements de curseur sont utiles comme un signal redondant pour l’information présentée ailleurs. Ne vous fiez pas à un changement de curseur comme seul moyen de communiquer avec l’utilisateur en particulier lorsque vous essayez de transmettre quelque chose qui est essentiel que l’utilisateur doit aborder.

#### <a name="progress-indicators"></a><a name="BKMK_NotSysProgressIndicators"></a>Indicateurs de progression
 Les indicateurs de progression sont importants pour donner aux utilisateurs la rétroaction au cours des processus qui prennent plus de quelques secondes à compléter. Les indicateurs de progression peuvent être affichés sur place (près du point de lancement de l’action en cours), dans une barre de statut intégrée, dans un dialogue modal, ou dans la barre d’état Visual Studio. Suivez les [indications](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ProgressIndicators) dans les indicateurs De progrès concernant leur utilisation et leur mise en œuvre.

#### <a name="visual-studio-notifications-window"></a><a name="BKMK_VSNotificationsToolWindow"></a>Fenêtre de notifications de studio visuel
 La fenêtre Visual Studio Notifications informe les développeurs sur les licences, l’environnement (Visual Studio), les extensions et les mises à jour. Les utilisateurs peuvent rejeter les notifications individuelles ou choisir d’ignorer certains types de notifications. La liste des notifications ignorées est gérée dans une page **Tools > Options.**

 La fenêtre Notifications n’est pas actuellement extensible.

 ![Fenêtre de notifications de Visual Studio](../../extensibility/ux-guidelines/media/0901-06_vsnotificationswindow.png "0901-06_VSNotificationsWindow")

 **Fenêtre d’outil Visual Studio Notifications**

#### <a name="error-list"></a><a name="BKMK_ErrorList"></a>Liste d’erreurs
 Une notification dans la liste d’erreurs indique les erreurs et les avertissements qui se sont produits au cours de la compilation et ou du processus de construction, et permet à l’utilisateur de naviguer dans le code à cette erreur de code spécifique.

 ![Liste d’erreurs](../../extensibility/ux-guidelines/media/0901-08_errorlist.png "0901-08_ErrorList")

 **Liste d’erreurs dans Visual Studio**

#### <a name="embedded-status-bars"></a><a name="BKMK_EmbeddedStatusBars"></a>Barres d’état intégrées
 Étant donné que la barre d’état IDE est dynamique, le contexte de sa région client étant défini à la fenêtre de document active et à la mise à jour des informations sur le contexte et/ou les réponses du système de l’utilisateur, il est difficile de maintenir un affichage continu de l’information ou de donner un statut sur les processus asynchrones à long terme. Par exemple, la barre d’état IDE n’est pas appropriée pour les notifications des résultats des essais pour plusieurs exécutions et/ou sélections d’éléments immédiatement exploitables. Il est important de conserver ces informations de statut dans le contexte du document ou de la fenêtre d’outil où l’utilisateur effectue une sélection ou démarre un processus.

 ![Barre d'état incorporée](../../extensibility/ux-guidelines/media/0901-09_embeddedstatusbar.png "0901-09_EmbeddedStatusBar")

 **Barre de statut intégrée dans Visual Studio**

#### <a name="windows-tray-notifications"></a><a name="BKMK_WindowsTray"></a>Notifications de plateau Windows
 La zone de notification Windows est à côté de l’horloge du système sur la barre des tâches Windows. De nombreux services publics et composants logiciels fournissent des icônes dans ce domaine afin que l’utilisateur puisse obtenir un menu contextuelle pour les tâches à l’échelle du système, comme changer la résolution de l’écran ou obtenir des mises à jour logicielles.

 Les notifications au niveau de l’environnement doivent être apparues dans le hub Visual Studio Notifications, et non dans la zone de notification Windows.

#### <a name="notification-bubbles"></a><a name="BKMK_NotificationBubbles"></a>Bulles de notification
 Les bulles de notification peuvent apparaître comme informations dans un éditeur/concepteur ou dans le cadre de la zone de notification Windows. L’utilisateur perçoit ces bulles comme des problèmes qu’ils peuvent résoudre plus tard, ce qui est un avantage pour les notifications non critiques. Les bulles sont inappropriées pour les informations critiques que l’utilisateur doit résoudre immédiatement. Si vous utilisez des bulles de notification dans Visual Studio, suivez les [conseils Windows Desktop pour les bulles de notification](/windows/desktop/uxguide/mess-notif).

 ![Bulle de notification](../../extensibility/ux-guidelines/media/0901-07_notificationbubbles.png "0901-07_NotificationBubbles")

 **Bulle de notification dans la zone de notification Windows utilisée pour Visual Studio**

## <a name="progress-indicators"></a><a name="BKMK_ProgressIndicators"></a>Indicateurs de progression

### <a name="overview"></a>Vue d'ensemble
 Les indicateurs de progression sont une partie importante d’un système de notification pour donner la rétroaction de l’utilisateur. Ils indiquent à l’utilisateur quand les processus et les opérations seront terminés. Les types d’indicateurs familiers comprennent les barres de progression, les curseurs de filature et les icônes animées. Le type et le placement d’un indicateur de progression dépendent du contexte, y compris ce qui est signalé et combien de temps le processus ou l’opération prendra pour terminer.

#### <a name="factors"></a>Facteurs
 Afin de déterminer quel type d’indicateur est approprié, vous devez déterminer les facteurs suivants.

1. **Calendrier :** durée de l’opération

2. **Modalité :** si l’opération est modale à l’environnement (verrouille l’interface utilisateur jusqu’à ce que le processus soit terminé)

3. **Persistant/transitoire :** si le résultat final des progrès doit être rapporté et/ou visible ultérieurement

4. **Déterminer/indéterminée :** si l’heure de fin et les progrès de l’opération peuvent être calculés

5. **Emplacement graphique/textuel :** si le progrès ou le processus est capturé en ligne, dans le corps d’un message, ou un contrôle spécifique, tel que le contrôle de l’arbre

6. **Proximité :** si les progrès doivent être à proximité de l’assurance-chômage à laquelle elle est liée. (Par exemple, peut-il être dans la barre d’état, qui pourrait être loin, ou doit-il être près du bouton qui a lancé le processus?)

#### <a name="determinate-progress"></a>Progrès déterminés

|Type de progression|Quand et comment utiliser|Notes|
|-------------------|-------------------------|-----------|
|Barre de progression (déterminée)|Durée prévue de >5 secondes.<br /><br /> Peut inclure la description textuelle des détails du processus.|**NE pas** intégrer le texte dans l’animation.|
|Barre d'informations|Messagerie associée à l’interface utilisateur contextuelle. Voir [Infobars](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars).<br /><br /> Peut inclure la description textuelle des détails du processus.|**N’utilisez pas** plusieurs infobars lorsque vous devez indiquer plusieurs processus. Utilisez plutôt des barres de progression empilées.|
|Fenêtre Sortie|Notification transitoire : processus de niveau d’application que l’utilisateur souhaite **examiner** les détails après l’achèvement.|**N’utilisez pas** si l’utilisateur devra se référer aux données plus tard.|
|Fichier journal|Associé à une notification intransiente dans les cas où il est important **d’enregistrer** des détails après l’achèvement.||
|Barre d'état|Notification transitoire : processus de niveau d’application dont l’utilisateur **n’aura pas besoin** de détails après l’achèvement.<br /><br /> Inclut une barre de progression intégrée.<br /><br /> Peut inclure la description textuelle des détails du processus.||

#### <a name="indeterminate-progress"></a>Progrès indéterminés

|Type de progression|Quand et comment utiliser|Notes|
|-------------------|-------------------------|-----------|
|Barre de progression (indéterminée)|Durée prévue de >5 secondes.<br /><br /> Peut inclure la description textuelle des détails du processus.|**NE pas** intégrer le texte dans l’animation.|
|Fourmis (points horizontaux animés)|Aller-retour au serveur.<br /><br /> Placé près du point de contexte sur le dessus du conteneur parent.|Ne pas utiliser si elle **n’est** pas parentée par conteneur entier.|
|Spinner (anneau de progrès)|Processus associé à l’interface utilisateur contextuelle, ou lorsque l’espace est une considération.<br /><br /> Peut inclure la description textuelle des détails du processus.||
|Barre d'informations|Messagerie associée à l’interface utilisateur contextuelle. Voir [Infobars](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars).|**N’utilisez pas** plusieurs infobars lorsque vous devez indiquer plusieurs processus. Utilisez plutôt des barres de progression empilées.|
|Fenêtre Sortie|Notification transitoire : processus de niveau d’application que l’utilisateur voudra **examiner** les détails après l’achèvement.|Ne pas utiliser pour **l’information** qui doit persister au cours des sessions.|
|Fichier journal|Associé à une notification intransiente dans les cas où il est important **d’enregistrer** des détails après l’achèvement.||
|Barre d'état|Notification transitoire : processus de niveau d’application dont l’utilisateur **n’aura pas besoin** de détails après l’achèvement.<br /><br /> Inclut la barre de progression intégrée.<br /><br /> Peut inclure la description textuelle des détails du processus.||

### <a name="progress-indicator-types"></a>Types d’indicateurs de progression

#### <a name="progress-bars"></a>Barres de progression

##### <a name="indeterminate"></a>Indéterminé
 ![Barre de progression indéterminée](../../extensibility/ux-guidelines/media/0901-04_indeterminate.png "0901-04_Indeterminate")

 **Barre de progression indéterminée**

 « Indéterminée » signifie que l’avancement global d’une opération ou d’un processus ne peut être déterminé. Utilisez des barres de progression indéterminées pour les opérations qui nécessitent un temps illimité ou qui accèdent à un nombre inconnu d’objets. Utilisez une description textuelle pour accompagner ce qui se passe. Utilisez les délais d’attente pour donner des limites aux opérations basées sur le temps. Les barres de progrès indéterminées utilisent des animations pour montrer que des progrès sont réalisés, mais ne fournissent aucune autre information. Ne choisissez pas une barre de progression indéterminée basée uniquement sur le manque possible de précision.

##### <a name="determinate"></a>Déterminée
 ![Barre de progression déterminée](../../extensibility/ux-guidelines/media/0901-05_determinate.png "0901-05_Determinate")

 **Barre de progression déterminée**

 « Déterminée » signifie qu’une opération ou un processus nécessite un délai délimité, même si ce temps ne peut pas être prédit avec précision. Indiquer clairement l’achèvement. Ne laissez pas une barre de progression aller à 100 pour cent à moins que l’opération a terminé. L’animation de barres de progression déterminée passe de 0 à 100 % à droite.

 Ne déplacez jamais l’indicateur de progression vers l’arrière au cours d’une opération. La barre doit avancer régulièrement lorsque l’opération commence et atteindre 100 % à la fin de l’opération. Le but de la barre de progression est de donner à l’utilisateur une idée de combien de temps l’opération entière prend, indépendamment du nombre d’étapes sont impliquées.

##### <a name="concurrent-reporting-stacked-progress-bars"></a>Rapports simultanés (barres de progression empilées)
 Si une opération prend beaucoup de temps - peut-être plusieurs minutes - alors deux barres de progression peuvent être utilisées, l’une qui montre les progrès globaux pour une opération et l’autre pour la progression de l’étape actuelle. Par exemple, si un programme d’installation copie de nombreux fichiers, une barre de progression peut être utilisée pour indiquer combien de temps prend l’ensemble du processus pendant qu’une seconde peut indiquer quel pourcentage du fichier ou de l’annuaire actuel est copié. Ne signalez pas plus de cinq opérations ou processus simultanés à l’aide de barres de progression empilées. Si vous avez plus de cinq opérations ou processus simultanés à signaler, utilisez un dialogue modal avec un bouton Annuler et signalez les détails de progression à la fenêtre de sortie.

##### <a name="textual-descriptions"></a>Descriptions textuelles
 Utilisez une description textuelle pour accompagner ce qui se passe et le temps estimé à l’achèvement. S’il est impossible de déterminer combien de temps une opération prendra, alors un meilleur choix pour donner des commentaires pourrait être une icône animée plutôt qu’une barre de progression.

 Visual Studio fournit une barre de progression standard dans la barre d’état qui peut être utilisé par n’importe quel produit intégré dans Visual Studio. Pour les descriptions textuelles de ce qui se passe pendant que la barre de progression est animée, le texte de barre d’état peut être mis à jour.

#### <a name="other-progress-indicators"></a>Autres indicateurs de progrès

##### <a name="ants-animated-horizontal-dots"></a>Fourmis (points horizontaux animés)
 ![Tirets de progression](../../extensibility/ux-guidelines/media/0903-01_ants.png "0903-01_Ants")

 Les « fourmis », des points horizontaux animés, fournissent une référence visuelle pour un processus de serveur aller-retour indéterminé.

##### <a name="spinner-progress-ring"></a>Spinner (anneau de progrès)
 ![Compteur de progression](../../extensibility/ux-guidelines/media/0903-02_spinner.png "0903-02_Spinner")

 Le filature (également connu sous le nom d'« anneau de progression ») est un indicateur de progression pour une durée indéterminée principalement utilisé par rapport à l’interface utilisateur contextuelle. Affichez un spinner à proximité de son contenu connexe, comme un en-tête de catégorie textuelle, une messagerie ou un contrôle.

##### <a name="cursor-feedback"></a>Rétroaction de Cursesor
 Pour les opérations qui prennent entre 2-7 secondes, fournir la rétroaction curseur. En règle générale, cela signifie utiliser le curseur d’attente fourni par le système d’exploitation. Pour obtenir des conseils, consultez l’article de MSDN [Cursors.Wait Property](/dotnet/api/system.windows.input.cursors.wait).

#### <a name="progress-indicator-locations"></a>Emplacements des indicateurs de progression

##### <a name="status-bar"></a>Barre d'état
 La barre d’état donne à votre application un endroit pour afficher des messages et des informations utiles à l’utilisateur sans interrompre le travail de l’utilisateur. Généralement affiché au bas d’une fenêtre, l’état de progression sera un volet de pointe d’outil qui comprend un message sur la mesure des progrès en combinaison avec un indicateur de barre de progression.

 ![Barre d'état avec barre de progression](../../extensibility/ux-guidelines/media/0903-03_statusbarprogressbar.png "0903-03_StatusBarProgressBar")

 **Barre d'état avec barre de progression**

 ![Barre d'état avec messagerie](../../extensibility/ux-guidelines/media/0903-04_statusbarmessage.png "0903-04_StatusBarMessage")

 **Barre d’état avec description textuelle**

##### <a name="infobar"></a>Barre d'informations
 Semblable à la barre d’état, la barre d’information fournit la notification contextuelle et la messagerie, qui peuvent également être jumelées avec des indicateurs de progression indéterminés tels que la barre de progression ou spinner. La barre d’information ne doit pas fournir des progrès de niveau granulaire ou une indication de progression déterminée. Voir [Infobars](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars).

 ![Barre d'informations avec messagerie et barre de progression](../../extensibility/ux-guidelines/media/0903-05_infobar.png "0903-05_InfoBar")

 **Infobar avec barre de progression et description textuelle**

 ![Barre d'informations à l'intérieur d'une fenêtre](../../extensibility/ux-guidelines/media/0903-06_infobarinwindow.png "0903-06_InfoBarInWindow")

##### <a name="inline"></a>En ligne
 L’indication de progression en ligne peut être représentée par n’importe lequel des types de chargeur de progression. Typiquement, l’indicateur de progression est jumelé avec la messagerie, mais ce n’est pas une exigence.

 ![Compteur de progression inline](../../extensibility/ux-guidelines/media/0903-07_inlinespinner.png "0903-07_InlineSpinner")

 **Spinner combiné avec la description textuelle**

 ![Barres de progression empilées inline](../../extensibility/ux-guidelines/media/0903-08_inlinestackedprogress.png "0903-08_InlineStackedProgress")

 **Barres de progression empilées déterminées**

 ![Messagerie de progression inline](../../extensibility/ux-guidelines/media/0903-09_inlinetext.png "0903-09_InlineText")

 **Server Explorer texte en ligne: Rafraîchissant ...**

##### <a name="tool-windows"></a>Fenêtres d’outil
 L’indication de progrès mondial est représentée par une barre de progression indéterminée placée directement en dessous de la barre d’outils.

 ![Barre de progression indéterminée globale](../../extensibility/ux-guidelines/media/0903-23_globalindeterminate.png "0903-23_GlobalIndeterminate")

 **Team Explorer global inde termate progress bar**

##### <a name="dialogs"></a>Boîtes de dialogue
 Les dialogues peuvent contenir n’importe lequel des types de chargeur de progression. Les indicateurs de progression peuvent être jumelés à la messagerie ainsi qu’à de multiples niveaux d’indication de progression pour représenter les processus granulaires et sous-traitants.

 ![Boîte de dialogue avec plusieurs types d'indicateurs de progression](../../extensibility/ux-guidelines/media/0903-11_dialog.png "0903-11_Dialog")

 **Dialogue Visual Studio avec des processus simultanés et de multiples types d’indicateurs de progression**

 ![Boîte de dialogue avec messagerie et chargeur de progression](../../extensibility/ux-guidelines/media/0903-12_dialog2.png "0903-12_Dialog2")

 **Dialogue visual Studio avec chargeur de progression et messagerie en ligne commandant**

##### <a name="document-well"></a>Bien documenter
 Le document peut bien afficher plusieurs types de chargeur de progression en combinaison avec les commandes.

 ![Messagerie de progression dans une zone de configuration de document](../../extensibility/ux-guidelines/media/0903-13_documentwell.png "0903-13_DocumentWell")

 **Barre de progression indéterminée en dessous de la barre d’outils**

##### <a name="output-window"></a>Fenêtre Sortie
 La fenêtre de sortie est appropriée pour la progression du processus de traitement et l’état de progression continue par messagerie textuelle en ligne. Vous devez utiliser la barre de statut ainsi que n’importe quel rapport de progression de fenêtre de sortie.

 ![Messagerie de progression dans une fenêtre Sortie](../../extensibility/ux-guidelines/media/0903-14_outputwindow.png "0903-14_OutputWindow")

 **Fenêtre de sortie avec l’état continu du processus et la messagerie d’attente**

## <a name="infobars"></a><a name="BKMK_Infobars"></a>Infobars (Infobars)

### <a name="overview"></a>Vue d'ensemble
 Infobars donner à l’utilisateur un indicateur proche de leur point d’attention et en utilisant le contrôle de l’infobar partagé assure la cohérence dans l’apparence visuelle et l’interaction.

 ![Barre d'informations](../../extensibility/ux-guidelines/media/0904-01_infobar.png "0904-01_Infobar")

 **Infobars en studio visuel**

#### <a name="appropriate-uses-for-an-infobar"></a>Utilisations appropriées pour une infobar

- Donner à l’utilisateur un message non-blocage mais important pertinent pour le contexte actuel

- Indiquer que l’interface utilisateur est dans un certain état ou une condition qui a des implications d’interaction, telles que le débogage historique

- Informer l’utilisateur que le système a détecté des problèmes, par exemple lorsqu’une extension cause des problèmes de performances

- Fournir à l’utilisateur un moyen d’agir facilement, par exemple lorsque l’éditeur détecte qu’un fichier a des onglets et des espaces mixtes

##### <a name="do"></a>À faire :

- Gardez le message infobar court et au point.

- Gardez le texte sur les liens et les boutons succincts.

- Assurez-vous que les options d’action que vous fournissez aux utilisateurs sont minimes, montrant uniquement les actions requises.

##### <a name="dont"></a>Ne pas:

- Utilisez une barre d’information pour offrir des commandes standard qui doivent être placées dans une barre d’outils.

- Utilisez une infobar à la place d’un dialogue modal.

- Créez un message flottant à l’extérieur d’une fenêtre.

- Utilisez plusieurs infobars à plusieurs endroits dans la même fenêtre.

#### <a name="can-multiple-infobars-show-at-the-same-time"></a>Plusieurs infobars peuvent-ils s’afficher en même temps ?
 Oui, plusieurs infobars peuvent s’afficher en même temps. Ils seront affichés dans le premier arrivé, premier servi commande avec la première infobar montrant sur le dessus et infobars supplémentaires montrant ci-dessous.

 L’utilisateur verra un maximum de trois infobars à la fois, après quoi, si plus d’infobars sont disponibles, la région infobar deviendra défilementable.

### <a name="creating-an-infobar"></a>Création d’une infobar
 L’infobar comporte quatre sections, de gauche à droite :

- **Icône:** C’est là que vous ajouteriez n’importe quelle icône que vous souhaitez afficher pour l’infobar, comme une icône d’avertissement.

- **Texte:** Vous pouvez ajouter du texte pour décrire le scénario /situation dans lequel l’utilisateur est, ainsi que des liens dans le texte, si nécessaire. N’oubliez pas de garder le texte succinct.

- **Actions:** Cette section doit contenir des liens et des boutons pour les actions que l’utilisateur peut prendre dans votre infobar.

- **Bouton de fermeture:** La dernière section à droite peut avoir un bouton proche.

#### <a name="creating-a-standard-infobar-in-managed-code"></a>Création d’une barre d’information standard dans le code géré
 La classe InfoBarModel peut être utilisée pour créer une source de données pour une infobar. Utilisez l’un de ces quatre constructeurs :

```
public InfoBarModel(IEnumerable<IVsInfoBarTextSpan> textSpans, ImageMoniker image = default(ImageMoniker), bool isCloseButtonVisible = true);

```

```
public InfoBarModel(string text, ImageMoniker image = default(ImageMoniker), bool isCloseButtonVisible = true);

```

```
public InfoBarModel(IEnumerable<IVsInfoBarTextSpan> textSpans, IEnumerable<IVsInfoBarActionItem> actionItems, ImageMoniker image = default(ImageMoniker), bool isCloseButtonVisible = true);

```

```
public InfoBarModel(string text, IEnumerable<IVsInfoBarActionItem> actionItems, ImageMoniker image = default(ImageMoniker), bool isCloseButtonVisible = true);
```

 Voici un exemple qui crée un InfoBarModel avec un certain texte avec un hyperlien, un bouton d’action, et une icône.

 ![Barre d'informations avec lien hypertexte](../../extensibility/ux-guidelines/media/0904-02_infobarhyperlink.png "0904-02_InfobarHyperlink")

```
var infoBar = new InfoBarModel(
    textSpans: new[]
    {
        new InfoBarTextSpan("This is a "),
        new InfoBarHyperlink("hyperlink"),
        new InfoBarTextSpan(" InfoBar.")
    },
    actionItems: new[]
    {
        new InfoBarButton("Click Me")
    },
    image: KnownMonikers.StatusInformation,
    isCloseButtonVisible: true);

```

#### <a name="creating-a-standard-infobar-in-native-code"></a>Création d’une barre d’information standard dans le code natif
 Implémentez l’interface IVsInfoBar afin de fournir une infobar à partir de code natif.

```
public interface IVsInfoBar
{
    IVsInfoBarActionItemCollection ActionItems { get; }
    ImageMoniker Image { get; }
    bool IsCloseButtonVisible { get; }
    IVsInfoBarTextSpanCollection TextSpans { get; }
}

```

#### <a name="getting-an-infobar-uielement-from-an-infobar"></a>Obtenir une interface utilisateur infobar d’une barre d’infobar
 La implémentation InfoBarModel ou IVsInfoBar sont des modèles de données qui doivent être transformés en interface utilisateur afin d’être indiqués dans l’interface utilisateur. Un UIElement peut être récupéré avec le service SVsInfoBarUIFactory/IVsInfoBarUIFactory.

```
private bool TryCreateInfoBarUI(IVsInfoBar infoBar, out IVsInfoBarUIElement uiElement)
{
    IVsInfoBarUIFactory infoBarUIFactory = serviceProvider.GetService(typeof(SVsInfoBarUIFactory)) as IVsInfoBarUIFactory;
    if (infoBarUIFactory == null)
    {
        uiElement = null;
        return false;
    }

    uiElement = infoBarUIFactory.CreateInfoBar(infoBar);
    return uiElement != null;
}
```

### <a name="placement"></a>Placement
 Les infobars peuvent être affichées dans un ou plusieurs des endroits suivants :

- Fenêtres d’outil

- Dans un onglet document

> [!IMPORTANT]
> Il est possible de positionner une barre d’info pour donner un message sur le contexte mondial. Cela apparaîtrait entre les barres d’outils et le document bien. Cela n’est pas recommandé parce qu’il cause des problèmes avec "sauter et secousse" de l’IDE et doit être évité à moins que absolument nécessaire et approprié.

#### <a name="placing-an-infobar-in-a-toolwindowpane"></a>Placer une barre d’information dans un ToolWindowPane
 La méthode ToolWindowPane.AddInfoBar (IVsInfoBar) peut être utilisée pour ajouter une infobar à une fenêtre d’outils. Cette API peut soit ajouter un IVsInfoBar (dont InfoBarModel est une implémentation par défaut), soit un IVsUIElement.

#### <a name="placing-an-infobar-in-a-document-or-non-toolwindowpane"></a>Placer une barre d’information dans un document ou un document non-ToolWindowPane
 Pour placer une infobar dans n’importe quel IVsWindowFrame, utilisez la propriété VSFPROPID_InfoBarHost pour obtenir l’IVsInfoBarHost pour le cadre, puis ajoutez l’interface utilisateur infobar.

```
private void AddInfoBar(IVsWindowFrame frame, IVsUIElement uiElement)
{
    IVsInfoBarHost infoBarHost;
    if (TryGetInfoBarHost(frame, out infoBarHost))
    {
        infoBarHost.AddInfoBar(uiElement);
    }
}
private bool TryGetInfoBarHost(IVsWindowFrame frame, out IVsInfoBarHost infoBarHost)
{
    object infoBarHostObj;
    if (ErrorHandler.Failed(frame.GetProperty((int)__VSFPROPID7.VSFPROPID_InfoBarHost, out infoBarHostObj)))
    {
        infoBarHost = null;
        return false;
    }

    infoBarHost = infoBarHostObj as IVsInfoBarHost;
    return infoBarHost != null;
}

```

#### <a name="placing-an-infobar-in-the-main-window"></a>Placer une barre d’infobar dans la fenêtre principale
 Pour placer une infobar dans la fenêtre principale, utilisez le VSSPROPID_MainWindowInfoBarHost du service IVsShell pour obtenir iVsInfoBarHost de la fenêtre principale, puis ajoutez l’interface utilisateur infobar.

### <a name="will-i-know-when-the-user-takes-action-in-my-infobar"></a>Saurai-je quand l’utilisateur prendra des mesures dans mon infobar ?
 Oui, nous retournerons chaque action événement à l’auteur infobar. Il appartient alors à l’auteur de l’infobar de prendre des mesures dans l’IDE en fonction de la sélection des utilisateurs dans l’infobar. Infobars sera automatiquement supprimé de l’hôte dont le bouton Close a été cliqué, mais un travail supplémentaire est nécessaire si d’autres infobars doivent être supprimés après la fermeture. La télémétrie devra également être enregistrée indépendamment par chaque infobar.

#### <a name="receiving-infobar-events-in-a-toolwindowpane"></a>Recevoir des événements infobar dans un ToolWindowPane
 ToolWindowPane a deux événements pour infobars. L’événement InfoBarClosed est soulevé lorsqu’une infobar dans l’ToolWindowPane est fermée. L’événement InfoBarActionItemClicked est soulevé lorsqu’un hyperlien ou un bouton à l’intérieur de l’infobar est cliqué.

#### <a name="receiving-infobar-events-directly-from-the-uielement"></a>Réception d’événements infobar directement de l’UIElement
 IVsInfoBarUIElement.Conseiller peut être utilisé pour vous abonner directement aux événements à partir de l’interface utilisateur d’une infobar. La mise en œuvre d’IVsInfoBarUIEvents permettra à l’auteur de recevoir des événements proches et clics.

```
public interface IVsInfoBarUIEvents
{
    void OnActionItemClicked(IVsInfoBarUIElement infoBarUIElement, IVsInfoBarActionItem actionItem);
    void OnClosed(IVsInfoBarUIElement infoBarUIElement);
}

```

## <a name="error-validation"></a><a name="BKMK_ErrorValidation"></a>Validation d’erreur
 Lorsqu’un utilisateur sais des informations qui ne sont pas acceptables, comme lorsqu’un champ requis est ignoré ou lorsque les données sont saisies dans le format incorrect, il est préférable d’utiliser la validation de contrôle ou la rétroaction près du contrôle au lieu d’utiliser un dialogue d’erreur popup blocage.

### <a name="field-validation"></a>Validation du champ
 La validation de la forme et du champ se compose de trois composants : un contrôle, une icône et une pointe d’outils. Bien que plusieurs types de contrôles puissent l’utiliser, une boîte de texte sera utilisée à titre d’exemple.

 ![Validation sur le terrain &#40;&#41;vierge](../../extensibility/ux-guidelines/media/0905-01_fieldvalidation.png "0905-01_FieldValidation")

 Si le champ est nécessaire, il devrait y avoir un texte filigrane indiquant `Environment.ControlEditRequiredBackground` `Environment.ControlEditRequiredHintText` ** \<les>requises** et l’arrière-plan du champ doit être jaune clair (VSColor: ) et le premier plan doit être gris (VSColor: ):

 ![Validation de champ avec étiquette « Obligatoire »](../../extensibility/ux-guidelines/media/0905-02_fieldvalidationrequired.png "0905-02_FieldValidationRequired")

 Le programme peut déterminer que le contrôle est dans un état de *contenu non valide entré* soit lorsque l’accent est mis sur un autre contrôle ou lorsque l’utilisateur clique sur un bouton de validation [OK] ou lorsque l’utilisateur enregistre le document ou le formulaire.

 Lorsque l’état de contenu invalide est déterminé, une icône apparaît soit à l’intérieur du contrôle, soit juste à côté. Une boîte à outils décrivant l’erreur doit apparaître sur le planet de l’icône ou du contrôle. En outre, une bordure d’un pixel devrait apparaître autour du contrôle qui crée l’état invalide.

 ![Spécifications de disposition de validation de champ](../../extensibility/ux-guidelines/media/0905-03_layoutspecs.png "0905-03_LayoutSpecs")

 **Spécifications de mise en page pour la validation de champ**

#### <a name="acceptable-variations-for-icon-location"></a>Variations acceptables pour l’emplacement de l’icône
 Il existe d’innombrables cas uniques dans lesquels les utilisateurs doivent être informés sur les erreurs de validation. Compte tenu du type de contrôle et de la configuration de l’interface utilisateur, choisissez le placement de l’icône adapté à votre situation.

 ![Emplacements acceptables pour l'emplacement de l'icône](../../extensibility/ux-guidelines/media/0905-04_iconlocation.png "0905-04_IconLocation")

 **Variations acceptables pour les emplacements d’icônes de validation de champ**

#### <a name="validation-requiring-a-round-trip-to-a-server-or-network-connection"></a>Validation nécessitant un aller-retour vers un serveur ou une connexion réseau
 Dans certains cas, un aller-retour vers le serveur est nécessaire pour vérifier le contenu, et il serait important de montrer les progrès de l’utilisateur, vérifié, et les états d’erreur. Le chiffre ci-dessous montre un exemple de ce cas et de l’interface utilisateur recommandée.

 ![Validation impliquant un aller-retour vers un serveur](../../extensibility/ux-guidelines/media/0905-05_roundtrip.png "0905-05_RoundTrip")

 **Validation impliquant un aller-retour vers un serveur**

 Notez qu’il faut fournir suffisamment d’espace disponible à la droite du contrôle afin de tenir compte de la « vérification... et le texte "Retry".

#### <a name="in-place-warning-text"></a>Texte d’avertissement sur place
 Lorsqu’il y a de la place pour mettre le message d’erreur près du contrôle dans un état d’erreur, cela est préférable à l’utilisation de l’outiltip seul.

 ![Dans&#45;'avertissement lieu](../../extensibility/ux-guidelines/media/0905-06_inplacewarning.png "0905-06_InPlaceWarning")

 **Texte d’avertissement sur place**

#### <a name="watermarks"></a>Filigranes
 Parfois, un contrôle ou une fenêtre entier est dans un état d’erreur. Dans cette situation, utilisez un filigrane pour indiquer l’erreur.

 ![Filigrane](../../extensibility/ux-guidelines/media/0905-07_watermark.png "0905-07_Watermark")

 **Validation de champ de filigrane**
