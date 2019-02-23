---
title: Notifications et progression pour Visual Studio | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f0ef65e9-0f1f-45f4-9f25-6e2398691168
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 694146672659d0a4370431040e84089088464f81
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56683166"
---
# <a name="notifications-and-progress-for-visual-studio"></a>Notifications et progression pour Visual Studio
##  <a name="BKMK_NotificationSystems"></a> Systèmes de notification

### <a name="overview"></a>Vue d'ensemble
 Il existe plusieurs façons d’informer l’utilisateur à ce qui se passe dans Visual Studio concernant leurs tâches de développement logiciel.

 Lors de l’implémentation de n’importe quel type de notification :

-   **Limiter le nombre de notifications au minimum** nombre effectif. Messages de notification doivent s’appliquer à la majorité des utilisateurs de Visual Studio ou à des utilisateurs d’une zone de fonctionnalité ou une fonctionnalité spécifique. Une utilisation excessive des notifications peut sidetrack l’utilisateur ou au contraire fragiliser perçue facilité d’utilisation du système.

-   **Assurez-vous de vous présentez des messages effacer et exploitables** que l’utilisateur peut utiliser pour appeler le contexte approprié pour effectuer des choix plus complexes et entreprendre une autre action.

-   **Présenter correctement les messages synchrones et asynchrones.** Notifications synchrones indiquer que quelque chose requiert une attention immédiate, tels que lorsqu’un service web tombe en panne ou un code d’exception est levée. L’utilisateur doit être informé de ces situations immédiatement d’une manière qui nécessite de leur avis, comme dans une boîte de dialogue modale. Notifications asynchrones sont celles que l’utilisateur doit connaître mais ne pas obligatoirement sur lequel agir immédiatement, comme à l’issue de l’exécution d’une opération de génération ou un déploiement de site web se termine. Ces messages doivent être plus ambiante et sans interrompre le flux de tâches de l’utilisateur.

-   **Utilisez les boîtes de dialogue modales uniquement lorsque cela est nécessaire pour empêcher l’utilisateur de passer outre** avant d’accuser réception du message ou une décision présenté dans la boîte de dialogue.

-   **Supprimer les notifications ambiantes lorsqu’ils ne sont plus valides.** Ne nécessitent pas l’utilisateur à faire disparaître une notification si elles ont déjà pris des mesures pour résoudre le problème qu’ils ont été informés.

-   **N’oubliez pas que les notifications peuvent entraîner de fausses corrélations.** Les utilisateurs peuvent penser qu’un ou plusieurs de leurs actions a déclenché une notification qu’en fait il y a aucune relation causale. Être clairement dans le message de notification sur le contexte, le déclencheur et la source de la notification.

### <a name="choosing-the-right-method"></a>Choisir la méthode appropriée
 Utilisez ce tableau pour vous aider à choisir la méthode appropriée pour informer l’utilisateur de votre message.

|Méthode|Utilisez|N’utilisez pas|
|------------|---------|----------------|
|[Boîtes de dialogue de message erreur modal](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ModalErrorMessageDialogs)|À utiliser lors de la réponse d’un utilisateur est requis avant de continuer.|N’utilisez pas lorsqu’il n’est pas nécessaire de bloquer l’utilisateur interrompt leur flux. Évitez d’utiliser des boîtes de dialogue modales s’il est possible d’afficher le message dans un autre moyen moins intrusif.|
|[Barre d’état IDE](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_IDEStatusBar)|Utilisation en l’absence des informations textuelles ambiantes concernant l’état d’un processus.|N’utilisez pas seul. Mieux utilisé conjointement avec un autre mécanisme de commentaires.|
|[Barre d’informations incorporée](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_EmbeddedInfobar)|Dans une fenêtre outil ou une fenêtre de document, utilisez à avertir de progression, état d’erreur, résultats et/ou des informations exploitables.|N’utilisez pas si les informations ne sont pas pertinentes pour l’emplacement où se trouve la barre d’informations.<br /><br /> N’utilisez pas en dehors d’une fenêtre de document/outil.|
|[Modifications de curseur de souris](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_MouseCursorChanges)|Peut être utilisé pour notifier qu’un processus se passe. Également utilisé pour avertir qu’il existe un changement d’état de la souris, tels que lorsque le glisser-déplacer est en cours ou que le pointeur se trouve dans un certain mode, par exemple le mode de dessin.|N’utilisez pas les modifications de progression courte ou si un mot du curseur est probablement (par exemple, lorsque lié aux parties d’un processus en cours d’exécution plus longs à la place de l’ensemble du processus).|
|[Indicateurs de progression](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_NotSysProgressIndicators)|À utiliser lorsque vous avez besoin pour signaler la progression (déterminé ou indéterminé). Il existe une variété de types d’indicateurs de progression et d’utilisation spécifiques pour chaque. Consultez [indicateurs de progression](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ProgressIndicators).||
|[Fenêtre de Visual Studio Notifications](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_VSNotificationsToolWindow)|La fenêtre Notifications n’est pas extensible publiquement. Toutefois, il est utilisé pour communiquer une plage de messages sur Visual Studio, y compris les problèmes critiques avec votre licence et les notifications d’information des mises à jour pour Visual Studio ou à des packages.|N’utilisez pas pour d’autres types de notifications.|
|[Liste d’erreurs](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ErrorList)|Lorsque le problème est lié directement à la solution actuellement ouverte de l’utilisateur rencontre un problème (erreur/avertissement / d’informations), il devra peut-être effectuer une opération sur le code.<br /><br /> Cela inclut, par exemple :<br /><br /> -Messages du compilateur (erreur/avertissement / d’informations)<br /><br /> -Messages d’analyseur/Diagnostic code sur le code<br /><br /> -Générer des messages<br /><br /> Peut être appropriée pour les problèmes liés aux fichiers projet ou solution, mais effectuez d’abord une indication de l’Explorateur de solutions.|N’utilisez pas pour les éléments qui n’ont pas de n’importe quelle relation au code de solution ouverte de l’utilisateur.|
|Notifications de l’éditeur : Ampoule|À utiliser lorsque vous avez un correctif disponible pour résoudre un problème qui existe dans le fichier ouvert.<br /><br /> Notez qu’ampoule doit également être utilisé pour héberger des Actions rapides qui sont effectuées sur le code de l’utilisateur à la demande, tels que des refactorisations, mais dans ce cas n’apparaîtra pas « style de notification ».|N’utilisez pas pour les éléments qui n’ont pas de n’importe quelle relation vers le fichier ouvert.|
|Notifications de l’éditeur : Tildes|Utilisez cette option pour avertir l’utilisateur à un problème avec une étendue particulière de leur code open (par exemple, une ligne ondulée rouge pour les erreurs).|N’utilisez pas pour les éléments qui ne sont pas liées à une étendue particulière de leur code ouvert.|
|[Barres d’état incorporée](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_EmbeddedStatusBars)|Permet de fournir d’état relatives au contenu ou processus au sein du contexte d’une fenêtre outil spécifique, la fenêtre de document ou la fenêtre de la boîte de dialogue.|N’utilisez pas pour les notifications de produit, des processus ou des éléments qui n’ont pas de n’importe quelle relation au contenu dans la fenêtre spécifique.|
|[Notifications de barre d’état Windows](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_WindowsTray)|Permet de faire apparaître des notifications pour les processus d’out-of-proc ou le Guide des applications.|N’utilisez pas pour les notifications qui sont pertinentes pour l’IDE.|
|[Bulles de notification](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_NotificationBubbles)|Utiliser pour informer d’un processus à distance ou de modifier **en dehors de** de l’IDE.|N’utilisez pas comme un moyen pour avertir l’utilisateur de processus **dans** l’IDE.|

### <a name="notification-methods"></a>Méthodes de notification

####  <a name="BKMK_ModalErrorMessageDialogs"></a> Boîtes de dialogue de message erreur modal
 Boîte de message d’erreur modal est utilisé pour afficher un message d’erreur qui requiert une confirmation ou action de l’utilisateur.

 ![Message d’erreur modal](../../extensibility/ux-guidelines/media/0901-01_modalerrormessage.png "0901-01_ModalErrorMessage")

 **Une boîte de dialogue modale erreur message avertissant l’utilisateur d’une chaîne de connexion non valide à une base de données**

####  <a name="BKMK_IDEStatusBar"></a> Barre d’état IDE
 La probabilité que les utilisateurs remarquent texte de barre d’état correspond à l’expérience d’ultra-rapide ordinateur et d’une expérience spécifique à la plate-forme Windows. La base de clients de Visual Studio a tendance à être expérimentés dans les deux domaines, bien que les utilisateurs de Windows même confirmés risquez de manquer des modifications dans la barre d’état. Par conséquent, la barre d’état est utilisée à titre d’information ou comme une file d’attente redondant pour les informations présentées ailleurs. N’importe quel type d’informations critiques doit être résolue immédiatement l’utilisateur doit être fournie dans une boîte de dialogue ou dans la fenêtre d’outil de Notifications.

 La barre d’état Visual Studio est conçue pour permettre plusieurs types d’informations à afficher. Il est divisé en régions pour vos commentaires, concepteur, barre de progression, l’animation et client.

 La zone de commentaires et de la zone du concepteur sont toujours visibles. La barre de progression et l’animation sont toujours des régions dynamiques et dépendent de contexte de l’utilisateur. La zone du concepteur a une largeur statique déterminée par la longueur de la chaîne extraite d’une ressource qui accompagne cet article pour le message texte. Cela permet la localisation de redimensionner la largeur sans nécessiter une modification du code. Pour l’anglais, la largeur de cette chaîne est environ 220 pixels. La zone du concepteur se comporte normalement et la zone de commentaires absorbe l’espace restant.

 La barre d’état est également colorée pour ajouter un attrait visuel et la valeur fonctionnel en communiquant différents changements d’état IDE tels que lorsque l’IDE est en mode débogage.

 ![Les modifications de couleur de la barre d’état IDE](../../extensibility/ux-guidelines/media/0901-02_idestatusbar.png "0901-02_IDEStatusBar")

 **Couleurs de barre d’état IDE**

####  <a name="BKMK_EmbeddedInfobar"></a> Barre d’informations incorporée
 Une barre d’informations peut servir d’informer l’utilisateur d’un état ou une condition en haut d’une fenêtre de document ou de la fenêtre outil. Il peut également offrir des commandes afin que l’utilisateur peut avoir un moyen de prendre des mesures. La barre d’informations est un contrôle de l’interpréteur de commandes standard. Évitez de créer votre propre, qui agissent et apparaissent incohérent avec d’autres utilisateurs dans l’IDE. Consultez [barres d’informations](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars) pour les détails d’implémentation et des conseils d’utilisation.

 ![Incorporé barre d’informations](../../extensibility/ux-guidelines/media/0901-03_embeddedinfobar.png "0901-03_EmbeddedInfobar")

 **Une barre d’informations incorporées dans une fenêtre de document, l’utilisateur que l’IDE est en mode débogage d’historique et l’éditeur ne répond pas, de la même façon, comme il le fait en mode de débogage standard de génération d’alertes.**

####  <a name="BKMK_MouseCursorChanges"></a> Modifications de curseur de souris
 Lorsque vous modifiez le curseur de souris, utiliser des couleurs qui sont liés au service VSColor et sont déjà associés avec le curseur. Curseur se transforme en peut être utilisé pour indiquer une opération en cours, ainsi que les zones où l’utilisateur pointe sur une cible qui peut être déplacée, déposée ou permet de sélectionner un objet d’accès.

 Utilisez le curseur de souris occupé/attente uniquement lorsque tout le temps processeur disponible doit être réservé pour une opération, empêcher l’utilisateur d’exprimer toute entrée supplémentaire. Dans la plupart des cas avec des applications bien écrites à l’aide du multithreading, les heures lorsque les utilisateurs ne peuvent pas l’exécution d’autres opérations doivent être rares.

 N’oubliez pas que le curseur se transforme est utiles comme une file d’attente redondant pour plus d’informations présentées ailleurs. Ne comptez pas sur une modification de curseur comme seul moyen de communiquer avec l’utilisateur, en particulier lorsque vous essayez de faire passer quelque chose qui est essentiel que l’utilisateur doit répondre.

####  <a name="BKMK_NotSysProgressIndicators"></a> Indicateurs de progression
 Indicateurs de progression sont importantes pour donner les commentaires d’utilisateurs pendant les processus qui prennent plus de quelques secondes. Indicateurs de progression peuvent être affichées sur place (près du point de lancement de l’action en cours), dans une barre d’état incorporée, dans la boîte de dialogue modale ou dans la barre d’état Visual Studio. Suivez les instructions de [indicateurs de progression](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ProgressIndicators) concernant leur utilisation et l’implémentation.

####  <a name="BKMK_VSNotificationsToolWindow"></a> Fenêtre de Visual Studio Notifications
 La fenêtre de Notifications de Visual Studio avertit les développeurs sur les licences, environnement (Visual Studio), extensions et mises à jour. Les utilisateurs peuvent fermer les notifications individuelles ou peuvent choisir d’ignorer certains types de notifications. La liste des notifications ignorées est gérée dans un **Outils > Options** page.

 La fenêtre Notifications n’est pas actuellement extensible.

 ![Fenêtre de Visual Studio Notifications](../../extensibility/ux-guidelines/media/0901-06_vsnotificationswindow.png "0901-06_VSNotificationsWindow")

 **Fenêtre de Visual Studio Notifications outil**

####  <a name="BKMK_ErrorList"></a> Liste d’erreurs
 Une notification dans la liste d’erreurs indiquent des erreurs et avertissements qui s’est produite pendant la compilation et ou processus de génération et permettant à l’utilisateur de naviguer dans le code pour cette erreur de code spécifique.

 ![Liste d’erreurs](../../extensibility/ux-guidelines/media/0901-08_errorlist.png "0901-08_ErrorList")

 **Liste d’erreurs dans Visual Studio**

####  <a name="BKMK_EmbeddedStatusBars"></a> Barres d’état incorporée
 Étant donné que la barre d’état IDE est dynamique, avec son contexte de région du client à la fenêtre de document active et à la mise à jour sur le contexte de l’utilisateur et/ou des réponses du système d’informations, il est difficile de maintenir un affichage d’informations en continu ou donner l’état sur à long terme processus asynchrones. Par exemple, la barre d’état IDE n’est pas appropriée pour les notifications de résultats de la série de tests pour plusieurs exécutions et/ou les sélections d’élément à une intervention immédiate. Il est important de conserver ces informations d’état dans le contexte de la fenêtre de document ou l’outil où l’utilisateur effectue une sélection ou démarre un processus.

 ![Barre d’état incorporée](../../extensibility/ux-guidelines/media/0901-09_embeddedstatusbar.png "0901-09_EmbeddedStatusBar")

 **Barre d’état incorporée dans Visual Studio**

####  <a name="BKMK_WindowsTray"></a> Notifications de barre d’état Windows
 Les zone de notification est en regard du système de Windows de l’horloge sur la barre des tâches Windows. De nombreux utilitaires et les composants logiciels fournissent des icônes dans cette zone afin que l’utilisateur peut obtenir un menu contextuel pour les tâches de l’échelle du système, telles que la modification de la résolution d’écran ou l’obtention de mises à jour logicielles.

 Notifications de niveau de l’environnement doivent être exposées dans le hub de Notifications de Visual Studio, pas la zone de notification Windows.

####  <a name="BKMK_NotificationBubbles"></a> Bulles de notification
 Les bulles de notification peuvent apparaître à titre d’information au sein d’un éditeur/concepteur ou dans le cadre de la zone de Notification de Windows. L’utilisateur perçoit à ces bulles en tant que les problèmes qu’ils peuvent résoudre plus tard, qui est un avantage pour les notifications non critiques. Bulles sont inappropriées pour que l’utilisateur doit résoudre immédiatement les informations critiques. Si vous utilisez des bulles de notification dans Visual Studio, suivez le [des conseils de bureau de Windows pour les bulles de notification](/windows/desktop/uxguide/mess-notif).

 ![Bulle de notification](../../extensibility/ux-guidelines/media/0901-07_notificationbubbles.png "0901-07_NotificationBubbles")

 **Bulle de notification dans la zone de Notification de Windows utilisée pour Visual Studio**

##  <a name="BKMK_ProgressIndicators"></a> Indicateurs de progression

### <a name="overview"></a>Vue d'ensemble
 Indicateurs de progression constituent une partie importante d’un système de notification pour donner les commentaires d’utilisateurs. Ils indiquent l’utilisateur de la fin de processus et des opérations. Types d’indicateurs familier incluent les barres de progression, les curseurs de rotation et les icônes animées. Le type et le positionnement d’un indicateur de progression varie selon le contexte, y compris ce qui est signalé et la durée pendant laquelle le processus ou une opération prendra fin.

#### <a name="factors"></a>Facteurs
 Afin de déterminer quel type d’indicateur est approprié, vous devez déterminer les facteurs suivants.

1.  **Minutage :** prendra de durée de l’opération

2.  **Modalité :** si l’opération est modale à l’environnement (verrous de l’interface utilisateur jusqu'à ce que le processus est terminé)

3.  **Permanent/temporaire :** si le résultat final de la progression doit être signalée et/ou visible à une date ultérieure

4.  **Déterminée/indéterminé :** indique si l’heure de fin d’opération et la progression peuvent être calculées

5.  **Emplacement de graphique/Textual :** si le processus ou progression est capturée inline, dans le corps d’un message ou un contrôle spécifique, comme le contrôle d’arborescence

6.  **Proximité :** indique si la progression doit être à proximité de l’interface utilisateur qui lui sont associés. (Par exemple, peut être dans la barre d’état, qui peut être éloigné, ou qu’il ne doit être proche de bouton qui a lancé le processus ?)

#### <a name="determinate-progress"></a>Progression déterminée

|Type de progression|Quand et comment utiliser|Notes|
|-------------------|-------------------------|-----------|
|Barre de progression (déterminée)|Durée d’attendue > 5 secondes.<br /><br /> Peut inclure une description textuelle des détails de processus.|**Ne** incorporer texte animation.|
|Barre d'informations|Messagerie associé à l’interface utilisateur contextuel. Consultez [barres d’informations](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars).<br /><br /> Peut inclure une description textuelle des détails de processus.|**Ne** utiliser plusieurs barres d’informations lorsque vous avez besoin indiquer plusieurs processus. Utilisez les barres de progression empilées à la place.|
|Fenêtre Sortie|Notification temporaire : processus au niveau de l’application que l’utilisateur souhaitez **Examinez** détails d’après l’achèvement.|**Ne** utiliser si l’utilisateur a besoin faire référence aux données plus tard.|
|Fichier journal|Associé à la notification intransient dans le cas lorsqu’il est important de **enregistrer** détails après l’achèvement.||
|Barre d'état|Notification temporaire : processus au niveau de l’application que l’utilisateur sera **inutile** détails d’après l’achèvement.<br /><br /> Inclut une barre de progression incorporé.<br /><br /> Peut inclure une description textuelle des détails de processus.||

#### <a name="indeterminate-progress"></a>Progression indéterminée

|Type de progression|Quand et comment utiliser|Notes|
|-------------------|-------------------------|-----------|
|Barre de progression (indéterminé)|Durée d’attendue > 5 secondes.<br /><br /> Peut inclure une description textuelle des détails de processus.|**Ne** incorporer texte animation.|
|ANTS (points animés horizontales)|Aller-retour au serveur.<br /><br /> Placé près du point de contexte entre le haut du conteneur parent.|**Ne** utiliser si ne pas apparentés en intégralité du conteneur.|
|Spinner (boucle de progression)|Processus associée à l’interface utilisateur contextuel, où l’espace est un facteur important.<br /><br /> Peut inclure une description textuelle des détails de processus.||
|Barre d'informations|Messagerie associé à l’interface utilisateur contextuel. Consultez [barres d’informations](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars).|**Ne** utiliser plusieurs barres d’informations lorsque vous avez besoin indiquer plusieurs processus. Utilisez les barres de progression empilées à la place.|
|Fenêtre Sortie|Notification temporaire : processus au niveau de l’application que l’utilisateur souhaiterez **Examinez** détails d’après l’achèvement.|**Ne** utiliser pour les informations qui doivent être conservés entre les sessions.|
|Fichier journal|Associé à la notification intransient dans le cas lorsqu’il est important de **enregistrer** détails après l’achèvement.||
|Barre d'état|Notification temporaire : processus au niveau de l’application que l’utilisateur sera **inutile** détails d’après l’achèvement.<br /><br /> Inclut la barre de progression incorporé.<br /><br /> Peut inclure une description textuelle des détails de processus.||

### <a name="progress-indicator-types"></a>Types d’indicateurs de progression

#### <a name="progress-bars"></a>Barres de progression

##### <a name="indeterminate"></a>Indeterminate
 ![Barre de progression indéterminée](../../extensibility/ux-guidelines/media/0901-04_indeterminate.png "0901-04_Indeterminate")

 **Barre de progression indéterminée**

 « Indéterminé » signifie que l’état d’avancement d’une opération ou le processus ne peut pas être déterminé. Utilisez les barres de progression indéterminée pour les opérations qui nécessitent une quantité illimitée de temps ou qui accèdent à un nombre inconnu d’objets. Utilisez une description textuelle pour accompagner ce qui se passe. Utiliser des délais d’attente pour donner des limites pour les opérations basées sur le temps. Barres de progression indéterminée utilisent des animations pour montrer que progression est en cours, mais fournissent pas d’autres informations. Ne choisissez pas une barre de progression indéterminée basée uniquement sur l’absence de possible de précision uniquement.

##### <a name="determinate"></a>Déterminée
 ![Barre de progression déterminée](../../extensibility/ux-guidelines/media/0901-05_determinate.png "0901-05_Determinate")

 **Barre de progression déterminée**

 « Déterminée » signifie qu’une opération ou un processus nécessite une durée limitée, même si ce laps de temps ne peut pas être prédits avec précision. Indiquer clairement l’achèvement. Ne laissez pas une barre de progression atteindre 100 pour cent, sauf si l’opération est terminée. Animation de barre de progression déterminée déplace gauche à droite de 0 à 100 %.

 Jamais déplacer l’indicateur de progression vers l’arrière pendant une opération. La barre doit avancer régulièrement lorsque l’opération commence et atteindre 100 % lorsqu’elle se termine. Le point de la barre de progression consiste à donner à l’utilisateur une idée de la durée pendant laquelle l’opération entière prend, quel que soit le nombre d’étapes impliqué.

##### <a name="concurrent-reporting-stacked-progress-bars"></a>Simultanées reporting (barres de progression empilées)
 Si une opération prendra un certain temps - peut-être plusieurs minutes - deux barres peuvent être utilisé, un qui affiche la progression globale pour une opération et l’autre pour la progression de l’étape actuelle. Par exemple, si un programme d’installation est une copie de fichiers, une barre de progression peut être utilisée pour indiquer la durée pendant laquelle l’intégralité du processus prend alors que la seconde peut indiquer quel pourcentage du fichier actuel ou le répertoire est copié. Ne signalez pas plus de cinq opérations simultanées ou processus à l’aide des barres de progression empilées. Si vous avez plus de cinq opérations simultanées ou processus au rapport, utilisez une boîte de dialogue modale avec un bouton Annuler et un rapport les détails de la progression dans la fenêtre Sortie.

##### <a name="textual-descriptions"></a>Descriptions textuelles
 Utilisez une description textuelle pour accompagner ce qui se passe et l’heure de fin estimée. S’il est impossible de déterminer la durée pendant laquelle une opération peut prendre, un meilleur choix pour fournir des commentaires peut être une icône animée plutôt qu’une barre de progression.

 Visual Studio fournit une barre de progression standard dans la barre d’état qui peut être utilisée par tous les produits intégrés à Visual Studio. Pour obtenir une description textuelle de ce qui se passe alors que la barre de progression est animée, vous pouvez mettre à jour le texte de barre d’état.

#### <a name="other-progress-indicators"></a>Autres indicateurs de progression

##### <a name="ants-animated-horizontal-dots"></a>ANTS (points animés horizontales)
 ![Progression ants](../../extensibility/ux-guidelines/media/0903-01_ants.png "0903-01_Ants")

 « Ants, » points horizontales animés, fournissent une représentation visuelle d’un processus serveur aller-retour indéterminé.

##### <a name="spinner-progress-ring"></a>Spinner (boucle de progression)
 ![Compteur de progression](../../extensibility/ux-guidelines/media/0903-02_spinner.png "0903-02_Spinner")

 La zone de sélection numérique (également appelé une « boucle de progression ») est un indicateur de progression indéterminée principalement utilisé en relation avec l’interface utilisateur contextuel. Afficher un compteur à proximité de son contenu associé, tel qu’un en-tête de catégorie textuelle, messagerie ou contrôle.

##### <a name="cursor-feedback"></a>Commentaire du curseur
 Pour les opérations qui prennent entre 2 à 7 secondes, fournir des commentaires de curseur. En règle générale, cela signifie que le curseur d’attente fourni par le système d’exploitation à l’aide de. Pour obtenir des instructions, consultez l’article MSDN [Cursors.Wait propriété](/dotnet/api/system.windows.input.cursors.wait).

#### <a name="progress-indicator-locations"></a>Emplacements d’indicateur de progression

##### <a name="status-bar"></a>Barre d'état
 La barre d’état donne à votre application à afficher des messages et des informations utiles à l’utilisateur sans interruption du travail de l’utilisateur. Généralement affiché au bas d’une fenêtre, état de progression sera un volet d’outils de pointe qui inclut un message concernant la mesure de la progression en association avec un indicateur de barre de progression.

 ![Barre d’état avec barre de progression](../../extensibility/ux-guidelines/media/0903-03_statusbarprogressbar.png "0903-03_StatusBarProgressBar")

 **Barre d’état avec barre de progression**

 ![Barre d’état avec messagerie](../../extensibility/ux-guidelines/media/0903-04_statusbarmessage.png "0903-04_StatusBarMessage")

 **Barre d’état avec le texte de description**

##### <a name="infobar"></a>Barre d'informations
 Semblable à la barre d’état, la barre d’informations fournit des notifications contextuelles et messagerie, ce qui peut également être associé aux indicateurs de progression indéterminée telles que la barre de progression ou le compteur. La barre d’informations ne doit pas fournir de progression de niveau granulaire ou indication de progression déterminée. Consultez [barres d’informations](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars).

 ![Barre d’informations avec messagerie et de la barre de progression](../../extensibility/ux-guidelines/media/0903-05_infobar.png "0903-05_InfoBar")

 **Barre d’informations avec la barre de progression et la description textuelle**

 ![Barre d’informations à l’intérieur d’une fenêtre](../../extensibility/ux-guidelines/media/0903-06_infobarinwindow.png "0903-06_InfoBarInWindow")

##### <a name="inline"></a>Inline
 Indication de la progression inline peut être représentée par les types de chargeur de progression. En général, l’indicateur de progression est associé avec la messagerie, mais cela n’est pas obligatoire.

 ![Compteur de progression inline](../../extensibility/ux-guidelines/media/0903-07_inlinespinner.png "0903-07_InlineSpinner")

 **Combiné avec description textuelle de compteur**

 ![Inline des barres de progression empilées](../../extensibility/ux-guidelines/media/0903-08_inlinestackedprogress.png "0903-08_InlineStackedProgress")

 **Barres de progression empilées déterminée**

 ![Messagerie de progression inline](../../extensibility/ux-guidelines/media/0903-09_inlinetext.png "0903-09_InlineText")

 **Texte d’inline de l’Explorateur de serveur : L’actualisation...**

##### <a name="tool-windows"></a>Fenêtres d’outil
 Indication de la progression globale est représentée par une barre de progression indéterminée positionnée directement sous la barre d’outils.

 ![Barre de progression indéterminée globale](../../extensibility/ux-guidelines/media/0903-23_globalindeterminate.png "0903-23_GlobalIndeterminate")

 **Barre de progression indéterminée globale de Team Explorer**

##### <a name="dialogs"></a>Boîtes de dialogue
 Boîtes de dialogue peuvent contenir tout type de chargeur de progression. Indicateurs de progression peuvent être associés à la messagerie ainsi qu’associés à plusieurs niveaux d’indication de progression pour représenter granulaire et les sous-processus.

 ![Boîte de dialogue avec plusieurs types d’indicateurs de progression](../../extensibility/ux-guidelines/media/0903-11_dialog.png "0903-11_Dialog")

 **Boîte de dialogue Visual Studio avec plusieurs types d’indicateurs de progression et les processus simultanés**

 ![Boîte de dialogue avec messagerie et chargeur de progression](../../extensibility/ux-guidelines/media/0903-12_dialog2.png "0903-12_Dialog2")

 **Boîte de dialogue Visual Studio avec les commandes inline de la messagerie et chargeur de progression**

##### <a name="document-well"></a>Document bien
 Le document peut également afficher plusieurs types de chargeur de progression en association avec des contrôles.

 ![Messagerie de progression dans document bien](../../extensibility/ux-guidelines/media/0903-13_documentwell.png "0903-13_DocumentWell")

 **Barre de progression indéterminée sous la barre d’outils**

##### <a name="output-window"></a>Fenêtre Sortie
 La fenêtre sortie est appropriée pour la gestion des processus progression et l’état de progression en cours via la messagerie textuelle inline. Vous devez utiliser la barre d’état, ainsi que n’importe quel rapport de progression de fenêtre de sortie.

 ![Messagerie de progression dans la fenêtre sortie](../../extensibility/ux-guidelines/media/0903-14_outputwindow.png "0903-14_OutputWindow")

 **Fenêtre de sortie avec l’état du processus en cours et attendez la messagerie**

##  <a name="BKMK_Infobars"></a> Barres d’informations

### <a name="overview"></a>Vue d'ensemble
 Barres d’informations donner à l’utilisateur un indicateur proche de leur point d’attention et l’utilisation du contrôle de barre d’informations partagées garantit la cohérence dans l’apparence visuelle et d’interaction.

 ![Infobar](../../extensibility/ux-guidelines/media/0904-01_infobar.png "0904-01_Infobar")

 **Barres d’informations dans Visual Studio**

#### <a name="appropriate-uses-for-an-infobar"></a>Conditions d’utilisation pour une barre d’informations

-   Pour donner à l’utilisateur un message non bloquant mais important pertinente dans le contexte actuel

-   Pour indiquer que l’interface utilisateur est dans un état ou une condition qui comporte certaines conséquences de l’interaction, telles que le débogage d’historique

-   Pour notifier l’utilisateur que le système a détecté des problèmes, tels que quand une extension est à l’origine des problèmes de performances

-   Pour fournir l’utilisateur permet de facilement prendre des mesures, telles que quand l’éditeur détecte qu’un fichier a mixte tabulations et espaces

##### <a name="do"></a>Procédez comme :

-   Conserver le texte de message de barre d’informations bref et au point.

-   Conserver le texte sur les liens et les boutons concise.

-   Vérifiez les options « action » que vous fournissez aux utilisateurs sont minimes, affichant uniquement les actions requises.

##### <a name="dont"></a>Ne pas :

-   Utilisez une barre d’informations pour offrir des commandes standards qui doivent être placés dans une barre d’outils.

-   Utilisez une barre d’informations à la place d’une boîte de dialogue modale.

-   Créer un message flottant en dehors d’une fenêtre.

-   Utiliser plusieurs barres d’informations dans plusieurs emplacements au sein de la même fenêtre.

#### <a name="can-multiple-infobars-show-at-the-same-time"></a>Plusieurs barres d’informations peuvent afficher en même temps ?
 Oui, plusieurs barres d’informations peut afficher en même temps. Ils seront affichera dans l’ordre premier arrivé, premier servi avec la première barre d’informations affichant sur montrant des barres d’informations principales et supplémentaires ci-dessous.

 L’utilisateur verra un maximum de trois barres d’informations à la fois, après laquelle, si les barres plus d’informations sont disponibles, la région de barre d’informations deviendra permettant le défilement.

### <a name="creating-an-infobar"></a>Création d’une barre d’informations
 La barre d’informations comporte quatre sections, de gauche à droite :

-   **Icône :** Il s’agit, vous devriez ajouter n’importe quelle icône voulez-vous afficher pour la barre d’informations, telles que d’une icône d’avertissement.

-   **Texte :** Vous pouvez ajouter le texte pour décrire l’utilisateur de scénario/situation se trouve, ainsi que des liens dans le texte, si nécessaire. Pensez à conserver le texte concise.

-   **Actions :** Cette section doit contenir des liens et des boutons pour les actions que l’utilisateur peut effectuer dans votre barre d’informations.

-   **Bouton Fermer :** La dernière section à droite peut avoir un bouton Fermer.

#### <a name="creating-a-standard-infobar-in-managed-code"></a>Création d’une barre d’informations standard dans le code managé
 La classe InfoBarModel peut être utilisée pour créer une source de données pour une barre d’informations. Utilisez une de ces quatre constructeurs :

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

 Voici un exemple qui crée un InfoBarModel avec du texte avec un lien hypertexte, un bouton d’action et une icône.

 ![Barre d’informations avec lien hypertexte](../../extensibility/ux-guidelines/media/0904-02_infobarhyperlink.png "0904-02_InfobarHyperlink")

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

#### <a name="creating-a-standard-infobar-in-native-code"></a>Création d’une barre d’informations standard en code natif
 Implémenter l’interface IVsInfoBar l’afin de fournir une barre d’informations à partir du code natif.

```
public interface IVsInfoBar
{
    IVsInfoBarActionItemCollection ActionItems { get; }
    ImageMoniker Image { get; }
    bool IsCloseButtonVisible { get; }
    IVsInfoBarTextSpanCollection TextSpans { get; }
}

```

#### <a name="getting-an-infobar-uielement-from-an-infobar"></a>Obtention d’une barre d’informations UIElement à partir d’une barre d’informations
 L’implémentation InfoBarModel ou IVsInfoBar sont des modèles de données qui doivent être convertis en un UIElement pour pouvoir apparaître dans l’interface utilisateur. Un UIElement peut être récupéré avec le service de l’élément SVsInfoBarUIFactory/IVsInfoBarUIFactory.

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

### <a name="placement"></a>Sélection élective
 Barres d’informations peuvent être affichées dans une ou plusieurs des emplacements suivants :

-   Fenêtres d’outil

-   Au sein d’un onglet de document

> [!IMPORTANT]
>  Il est possible de placer une barre d’informations pour donner un message sur le contexte global. Cela s’affiche entre les barres d’outils et le document bien. Cela n’est pas recommandée, car cela entraîne des problèmes avec le « saut et jerk » de l’IDE et doit être évitée, sauf si cela est absolument nécessaire et approprié.

#### <a name="placing-an-infobar-in-a-toolwindowpane"></a>Placer une barre d’informations dans un ToolWindowPane
 La méthode ToolWindowPane.AddInfoBar(IVsInfoBar) peut être utilisée pour ajouter une barre d’informations à une fenêtre outil. Cette API peut ajouter un IVsInfoBar (le InfoBarModel est une implémentation par défaut), ou un IVsUIElement.

#### <a name="placing-an-infobar-in-a-document-or-non-toolwindowpane"></a>Placer une barre d’informations dans un document ou un non ToolWindowPane
 Pour placer une barre d’informations dans les IVsWindowFrame, utilisez la propriété VSFPROPID_InfoBarHost pour obtenir le IVsInfoBarHost pour le frame, puis ajoutez la barre d’informations UIElement.

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

#### <a name="placing-an-infobar-in-the-main-window"></a>Placer une barre d’informations dans la fenêtre principale
 Pour placer une barre d’informations dans la fenêtre principale, le VSSPROPID_MainWindowInfoBarHost du service IVsShell permet d’obtenir IVsInfoBarHost la fenêtre principale, puis ajoutez la barre d’informations UIElement à celui-ci.

### <a name="will-i-know-when-the-user-takes-action-in-my-infobar"></a>Savoir quand l’utilisateur prend des mesures dans ma barre d’informations ?
 Oui, nous y reviendrons chaque action d’événement l’auteur de la barre d’informations. Il est ensuite jusqu'à l’auteur de la barre d’informations pour prendre des mesures dans l’IDE en fonction de sélection de l’utilisateur dans la barre d’informations. Barres d’informations seront automatiquement supprimés de l’hôte de l’utilisateur a cliqué sur le bouton Fermer dont, mais le travail supplémentaire est nécessaire si les autres barres d’informations devoir être supprimées après la ferme. Données de télémétrie devrez également être enregistrés indépendamment par chaque barre d’informations.

#### <a name="receiving-infobar-events-in-a-toolwindowpane"></a>Réception d’événements de la barre d’informations dans un ToolWindowPane
 ToolWindowPane comporte deux événements pour les barres d’informations. L’événement InfoBarClosed est déclenché lorsqu’une barre d’informations dans le ToolWindowPane est fermée. L’événement InfoBarActionItemClicked est déclenché lorsque l’utilisateur clique sur un lien hypertexte ou un bouton à l’intérieur de la barre d’informations.

#### <a name="receiving-infobar-events-directly-from-the-uielement"></a>Réception d’événements de la barre d’informations directement à partir de UIElement
 IVsInfoBarUIElement.Advise permet de s’abonner aux événements directement à partir d’UIElement d’une barre d’informations. Implémentation IVsInfoBarUIEvents permettra à l’auteur de fermeture de réception et événements de clic.

```
public interface IVsInfoBarUIEvents
{
    void OnActionItemClicked(IVsInfoBarUIElement infoBarUIElement, IVsInfoBarActionItem actionItem);
    void OnClosed(IVsInfoBarUIElement infoBarUIElement);
}

```

##  <a name="BKMK_ErrorValidation"></a> Validation des erreurs
 Lorsqu’un utilisateur entre des informations qui ne sont pas acceptables, par exemple quand un champ obligatoire est ignoré, ou lorsque les données entrées dans le format est incorrect, il est préférable de validation de contrôle d’utilisation ou des commentaires près du contrôle au lieu d’utiliser une boîte de dialogue Erreur blocage du menu contextuel.

### <a name="field-validation"></a>Validation de champ
 Validation de formulaire et le champ se compose de trois composants : un contrôle, une icône et une info-bulle. Bien que plusieurs types de contrôles peuvent utiliser cela, une zone de texte est utilisée comme exemple.

 ![Validation du champ &#40;vide&#41;](../../extensibility/ux-guidelines/media/0905-01_fieldvalidation.png "0905-01_FieldValidation")

 Si le champ est obligatoire, il doit y avoir indiquant que le texte de filigrane  **\<requis >** et l’arrière-plan du champ doit être clair jaune (VSColor : `Environment.ControlEditRequiredBackground`) et de premier plan doit être gris (VSColor : `Environment.ControlEditRequiredHintText`) :

 ![Validation avec l’étiquette « Obligatoire » du champ](../../extensibility/ux-guidelines/media/0905-02_fieldvalidationrequired.png "0905-02_FieldValidationRequired")

 Le programme peut déterminer que le contrôle est dans un état de *contenu non valide entrée* lorsque le focus est déplacé vers un autre contrôle ou lorsque l’utilisateur clique sur un bouton de validation [OK] ou lorsque l’utilisateur enregistre le document ou le formulaire.

 Lorsque l’état de contenu non valide est déterminé, une icône s’affiche dans le contrôle ou simplement en regard de celle-ci. Une info-bulle décrivant l’erreur doit apparaître sur le pointage de l’icône ou le contrôle. En outre, une bordure de 1 pixel doit apparaître autour du contrôle qui crée l’état non valide.

 ![Spécifications de disposition de validation de champ](../../extensibility/ux-guidelines/media/0905-03_layoutspecs.png "0905-03_LayoutSpecs")

 **Spécifications de disposition pour la validation de champ**

#### <a name="acceptable-variations-for-icon-location"></a>Variations acceptables pour l’emplacement de l’icône
 Il existe un nombre incalculable de cas unique dans lequel les utilisateurs doivent être informés sur les erreurs de validation. Si l'on considère le type de contrôle et la configuration de l’interface utilisateur, choisissez le positionnement de l’icône correspondant à votre situation.

 ![Emplacements acceptables pour l’emplacement de l’icône](../../extensibility/ux-guidelines/media/0905-04_iconlocation.png "0905-04_IconLocation")

 **Variations acceptables pour les emplacements d’icône de validation de champ**

#### <a name="validation-requiring-a-round-trip-to-a-server-or-network-connection"></a>Validation nécessitant un aller-retour vers un serveur ou la connexion réseau
 Dans certains cas, un aller-retour vers le serveur est nécessaire pour vérifier le contenu, et il est important de montrer la progression de l’utilisateur, vérifié et les États d’erreur. La figure ci-dessous montre un exemple de ce cas et de l’interface utilisateur recommandée.

 ![Validation impliquant un aller-retour vers un serveur](../../extensibility/ux-guidelines/media/0905-05_roundtrip.png "0905-05_RoundTrip")

 **Validation impliquant un aller-retour vers un serveur**

 Notez que suffisamment d’espace disponible à droite du contrôle doit être fournie pour prendre en charge le texte « Vérification... » et « Réessayer ».

#### <a name="in-place-warning-text"></a>Texte d’avertissement sur place
 Lorsque l’espace disponible pour placer le message d’erreur proche du contrôle dans un état d’erreur est, il est préférable à l’utilisation de l’info-bulle uniquement.

 ![Dans&#45;placer avertissement](../../extensibility/ux-guidelines/media/0905-06_inplacewarning.png "0905-06_InPlaceWarning")

 **Texte d’avertissement sur place**

#### <a name="watermarks"></a>Filigranes
 Parfois, un contrôle entier ou une fenêtre est dans un état d’erreur. Dans ce cas, utilisez un filigrane pour indiquer l’erreur.

 ![Watermark](../../extensibility/ux-guidelines/media/0905-07_watermark.png "0905-07_Watermark")

 **Validation de champ de filigrane**