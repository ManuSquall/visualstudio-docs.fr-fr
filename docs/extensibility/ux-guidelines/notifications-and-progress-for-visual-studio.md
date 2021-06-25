---
title: Notifications et progression pour Visual Studio | Microsoft Docs
description: Découvrez les différentes façons d’informer les utilisateurs de ce qui se passe dans Visual Studio en ce qui concerne leurs tâches de développement logiciel.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: f0ef65e9-0f1f-45f4-9f25-6e2398691168
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 994a315d04b06d1998a8c8e0c4291b6a4c54cb61
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902239"
---
# <a name="notifications-and-progress-for-visual-studio"></a>Notifications et progression pour Visual Studio
## <a name="notification-systems"></a><a name="BKMK_NotificationSystems"></a> Systèmes de notification

### <a name="overview"></a>Vue d’ensemble
 Il existe plusieurs façons d’informer l’utilisateur de ce qui se passe dans Visual Studio en ce qui concerne ses tâches de développement logiciel.

 Lors de l’implémentation d’un type de notification :

- **Conservez le nombre de notifications au** nombre d’effectifs minimal. Les messages de notification doivent s’appliquer à la majorité des utilisateurs de Visual Studio ou aux utilisateurs d’une fonctionnalité ou d’un domaine de fonctionnalités spécifique. Une utilisation excessive des notifications peut Sidetrack l’utilisateur ou réduire la facilité d’utilisation du système.

- **Veillez à présenter des messages clairs et exploitables** que l’utilisateur peut utiliser pour appeler le contexte approprié pour effectuer des choix plus complexes et prendre des mesures supplémentaires.

- **Présentez les messages synchrones et asynchrones de manière appropriée.** Les notifications synchrones indiquent que des éléments nécessitent une attention immédiate, par exemple lorsqu’un service Web se bloque ou qu’une exception de code est levée. L’utilisateur doit être informé de ces situations immédiatement d’une manière qui nécessite son entrée, par exemple dans une boîte de dialogue modale. Les notifications asynchrones sont celles que l’utilisateur doit connaître mais n’ont pas besoin d’agir immédiatement, par exemple quand une opération de génération est terminée ou si un déploiement de site Web se termine. Ces messages doivent être plus ambiants et ne pas interrompre le déroulement des tâches de l’utilisateur.

- **Utilisez les boîtes de dialogue modales uniquement lorsque cela est nécessaire pour empêcher l’utilisateur d’effectuer des actions supplémentaires** avant d’accuser réception du message ou de prendre une décision présentée dans la boîte de dialogue.

- **Supprimer les notifications ambiantes lorsqu’elles ne sont plus valides.** Ne demandez pas à l’utilisateur de rejeter une notification si elle a déjà pris une mesure pour résoudre le problème à propos duquel elle a été notifiée.

- **Sachez que les notifications peuvent entraîner des fausses corrélations.** Les utilisateurs peuvent croire qu’une ou plusieurs de leurs actions ont déclenché une notification alors qu’il n’y avait pas de relation causale. Soyez clair dans le message de notification concernant le contexte, le déclencheur et la source de la notification.

### <a name="choosing-the-right-method"></a>Choix de la méthode appropriée
 Utilisez ce tableau pour vous aider à choisir la méthode appropriée pour notifier l’utilisateur de votre message.

|Méthode|Utiliser|À ne pas utiliser|
|------------|---------|----------------|
|[Boîtes de dialogue de message d’erreur modal](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ModalErrorMessageDialogs)|Utilisez quand une réponse de l’utilisateur est requise avant de continuer.|N’utilisez pas lorsque vous n’avez pas besoin de bloquer l’utilisateur et d’interrompre son acheminement. Évitez d’utiliser des boîtes de dialogue modales s’il est possible d’afficher le message d’une manière moins intrusive.|
|[Barre d’État IDE](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_IDEStatusBar)|À utiliser en cas d’informations textuelles ambiantes relatives à l’état d’un processus.|N’utilisez pas seul. Idéal avec un autre mécanisme de commentaires.|
|[Barre d'informations incorporée](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_EmbeddedInfobar)|Dans une fenêtre outil ou une fenêtre de document, utilisez pour notifier la progression, l’état d’erreur, les résultats et/ou les informations exploitables.|N’utilisez pas si les informations ne sont pas pertinentes à l’emplacement où la barre d’informations est placée.<br /><br /> N’utilisez pas l’extérieur d’une fenêtre de document ou d’outil.|
|[Modifications du curseur de la souris](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_MouseCursorChanges)|Peut être utilisé pour indiquer qu’un processus est en cours d’utilisation. Permet également de signaler qu’un changement d’État se présente dans la souris, par exemple lorsque le glisser-déplacer est en cours ou que le curseur de la souris est dans un certain mode, tel que le mode dessin.|N’utilisez pas pour les modifications de progression courtes ou si le curseur est très probable (par exemple, lorsqu’il est lié à des parties d’un processus dont l’exécution est plus longue plutôt qu’à l’ensemble du processus).|
|[Indicateurs de progression](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_NotSysProgressIndicators)|Utilisez lorsque vous avez besoin de signaler la progression (arrêt ou indéterminé). Il existe un grand nombre de types d’indicateurs de progression et une utilisation spécifique pour chacun d’entre eux. Consultez [indicateurs de progression](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ProgressIndicators).||
|[Fenêtre de notifications de Visual Studio](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_VSNotificationsToolWindow)|La fenêtre notifications n’est pas extensible publiquement. Toutefois, il est utilisé pour communiquer une série de messages sur Visual Studio, y compris les problèmes critiques liés à votre licence et les notifications d’information des mises à jour de Visual Studio ou des packages.|Ne pas utiliser pour d’autres types de notifications.|
|[Liste d’erreurs](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ErrorList)|Lorsque le problème se réfère directement à la solution actuellement ouverte de l’utilisateur qui rencontre un problème (erreur/avertissement/info), il peut être amené à agir sur le code.<br /><br /> Cela inclut, par exemple :<br /><br /> -Messages du compilateur (erreur/avertissement/info)<br /><br /> -Analyseur de code/messages de diagnostic sur le code<br /><br /> -Messages de génération<br /><br /> Peut convenir pour des problèmes liés aux fichiers de projet ou de solution, mais envisagez d’abord une indication de Explorateur de solutions.|N’utilisez pas pour les éléments qui n’ont pas de relation avec le code de solution ouvert de l’utilisateur.|
|Notifications de l’éditeur : ampoule|Utilisez lorsque vous avez un correctif disponible pour résoudre un problème qui existe dans le fichier ouvert.<br /><br /> Notez que l’ampoule doit également être utilisée pour héberger les actions rapides effectuées sur le code de l’utilisateur à la demande, telles que les refactorisations, mais dans ce cas, n’apparaît pas « style de notification ».|N’utilisez pas pour les éléments qui n’ont pas de relation avec le fichier ouvert.|
|Notifications de l’éditeur : tildes|Utilisez pour alerter l’utilisateur en cas de problème avec une étendue particulière de son code ouvert (par exemple, un tilde rouge pour les erreurs).|N’utilisez pas pour les éléments qui ne sont pas liés à une étendue particulière de leur code ouvert.|
|[Barres d’état incorporées](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_EmbeddedStatusBars)|Utilisez pour fournir l’état relatif au contenu ou au processus dans le contexte d’une fenêtre outil spécifique, d’une fenêtre de document ou d’une fenêtre de boîte de dialogue.|Ne pas utiliser pour les notifications de produit générales, les processus ou les éléments qui n’ont pas de relation avec le contenu dans la fenêtre spécifique.|
|[Notifications de la barre d’État Windows](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_WindowsTray)|À utiliser pour les notifications de surface pour les processus hors processus ou les applications auxiliaires.|Ne pas utiliser pour les notifications pertinentes pour l’IDE.|
|[Bulles de notification](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_NotificationBubbles)|Utilisez pour notifier un processus distant ou une modification **en dehors** de l’IDE.|N’utilisez pas comme moyen de notifier l’utilisateur de processus **au sein** de l’IDE.|

### <a name="notification-methods"></a>Méthodes de notification

#### <a name="modal-error-message-dialogs"></a><a name="BKMK_ModalErrorMessageDialogs"></a> Boîtes de dialogue de message d’erreur modal
 Une boîte de dialogue de message d’erreur modale est utilisée pour afficher un message d’erreur qui requiert la confirmation ou l’action de l’utilisateur.

 ![Message d'erreur modal](../../extensibility/ux-guidelines/media/0901-01_modalerrormessage.png "0901-01_ModalErrorMessage")

 **Boîte de dialogue de message d’erreur modal avertissant l’utilisateur d’une chaîne de connexion non valide à une base de données**

#### <a name="ide-status-bar"></a><a name="BKMK_IDEStatusBar"></a> Barre d’État IDE
 La probabilité que les utilisateurs remarquent le texte de barre d’état correspond à leur expérience d’ordinateur tout autour et à l’expérience spécifique de la plate-forme Windows. La base du client Visual Studio a tendance à être expérimentée dans les deux domaines, bien que même les utilisateurs de Windows compétents puissent manquer des modifications dans la barre d’État. Par conséquent, la barre d’État est mieux utilisée à des fins d’information ou en tant que pile redondante pour les informations présentées ailleurs. Tous les types d’informations critiques que l’utilisateur doit résoudre immédiatement doivent être fournis dans une boîte de dialogue ou dans la fenêtre de l’outil notifications.

 La barre d’état de Visual Studio est conçue pour permettre l’affichage de plusieurs types d’informations. Elle est divisée en régions pour les commentaires, les concepteurs, les barres de progression, les animations et les clients.

 La région de commentaires et la région du concepteur sont toujours visibles. La barre de progression et les régions d’animation sont toujours dynamiques et basées sur le contexte de l’utilisateur. La zone du concepteur a une largeur statique déterminée par la longueur de la chaîne extraite d’une ressource associée pour le message texte. Cela permet à la localisation de redimensionner la largeur sans nécessiter de modification du code. Pour l’anglais, la largeur de cette chaîne est environ 220 pixels. La zone du concepteur se comportera normalement et la région de commentaires absorbra l’espace restant.

 La barre d’État est également colorée pour ajouter un intérêt visuel et une valeur fonctionnelle en communiquant différentes modifications de l’état de l’IDE, comme lorsque l’IDE est en mode débogage.

 ![Modifications de couleur de la barre d'état IDE](../../extensibility/ux-guidelines/media/0901-02_idestatusbar.png "0901-02_IDEStatusBar")

 **Couleurs de la barre d’État IDE**

#### <a name="embedded-infobar"></a><a name="BKMK_EmbeddedInfobar"></a> Barre d’informations incorporée
 Une barre d’informations peut être utilisée en haut d’une fenêtre de document ou d’une fenêtre outil pour informer l’utilisateur d’un État ou d’une condition. Il peut également offrir des commandes qui permettent à l’utilisateur de prendre facilement des mesures. La barre d’informations est un contrôle d’interpréteur de commandes standard. Évitez de créer votre propre, qui agira et apparaîtra incohérent avec les autres dans l’IDE. Pour plus d’informations sur l’implémentation et des instructions d’utilisation, consultez [barres](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars) .

 ![Barre d'informations incorporée](../../extensibility/ux-guidelines/media/0901-03_embeddedinfobar.png "0901-03_EmbeddedInfobar")

 **Une barre d’informations incorporée dans une fenêtre de document, qui avertit l’utilisateur que l’IDE est en mode de débogage d’historique et que l’éditeur ne répond pas de la même façon que dans le mode de débogage standard.**

#### <a name="mouse-cursor-changes"></a><a name="BKMK_MouseCursorChanges"></a> Modifications du curseur de la souris
 Lorsque vous modifiez le curseur de la souris, utilisez des couleurs qui sont liées au service VSColor et qui sont déjà associées au curseur. Les modifications de curseur peuvent être utilisées pour indiquer une opération en cours, ainsi que des zones d’accès où l’utilisateur pointe sur une cible qui peut être glissée, déposée ou utilisée pour sélectionner un objet.

 Utilisez le curseur de la souris occupé/Wait uniquement lorsque tout le temps processeur disponible doit être réservé pour une opération, empêchant ainsi l’utilisateur d’exprimer d’autres entrées. Dans la plupart des cas, avec des applications bien écrites utilisant le multithreading, les moments où les utilisateurs sont empêchés d’exécuter d’autres opérations doivent être rares.

 Gardez à l’esprit que les modifications de curseur sont utiles en tant que pile redondante pour les informations présentées ailleurs. Ne vous fiez pas à un changement de curseur en tant que seul moyen de communiquer avec l’utilisateur, en particulier lors de la tentative de transmission d’un point essentiel que l’utilisateur doit traiter.

#### <a name="progress-indicators"></a><a name="BKMK_NotSysProgressIndicators"></a> Indicateurs de progression
 Les indicateurs de progression sont importants pour donner aux utilisateurs des commentaires pendant les processus qui prennent plus de quelques secondes. Les indicateurs de progression peuvent être affichés sur place (près du point de lancement de l’action en cours), dans une barre d’État incorporée, dans une boîte de dialogue modale ou dans la barre d’état de Visual Studio. Suivez les instructions des [indicateurs de progression](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ProgressIndicators) concernant leur utilisation et leur implémentation.

#### <a name="visual-studio-notifications-window"></a><a name="BKMK_VSNotificationsToolWindow"></a> Fenêtre notifications Visual Studio
 La fenêtre de notifications Visual Studio informe les développeurs sur les licences, l’environnement (Visual Studio), les extensions et les mises à jour. Les utilisateurs peuvent ignorer des notifications individuelles ou choisir d’ignorer certains types de notifications. La liste des notifications ignorées est gérée dans une page **outils > options** .

 La fenêtre notifications n’est pas extensible actuellement.

 ![Fenêtre de notifications de Visual Studio](../../extensibility/ux-guidelines/media/0901-06_vsnotificationswindow.png "0901-06_VSNotificationsWindow")

 **Fenêtre outil de notifications Visual Studio**

#### <a name="error-list"></a><a name="BKMK_ErrorList"></a> Liste d’erreurs
 Une notification dans la liste d’erreurs indique des erreurs et des avertissements qui se sont produits pendant la compilation et le processus de génération, et permet à l’utilisateur de naviguer dans le code vers cette erreur de code spécifique.

 ![Liste d’erreurs](../../extensibility/ux-guidelines/media/0901-08_errorlist.png "0901-08_ErrorList")

 **Liste d’erreurs dans Visual Studio**

#### <a name="embedded-status-bars"></a><a name="BKMK_EmbeddedStatusBars"></a> Barres d’état incorporées
 La barre d’État IDE étant dynamique, le contexte de la région du client étant défini sur la fenêtre de document active et la mise à jour des informations sur le contexte de l’utilisateur et/ou les réponses du système, il est difficile de conserver un affichage continu des informations ou d’obtenir l’état des processus asynchrones à long terme. Par exemple, la barre d’État IDE n’est pas appropriée pour les notifications de résultats de la série de tests pour plusieurs exécutions et/ou sélections immédiates d’éléments actionnables. Il est important de conserver ces informations d’État dans le contexte de la fenêtre de document ou d’outil dans laquelle l’utilisateur effectue une sélection ou démarre un processus.

 ![Barre d'état incorporée](../../extensibility/ux-guidelines/media/0901-09_embeddedstatusbar.png "0901-09_EmbeddedStatusBar")

 **Barre d’État incorporée dans Visual Studio**

#### <a name="windows-tray-notifications"></a><a name="BKMK_WindowsTray"></a> Notifications de la barre d’État Windows
 La zone de notification Windows se trouve à côté de l’horloge système dans la barre des tâches Windows. De nombreux utilitaires et composants logiciels fournissent des icônes dans cette zone afin que l’utilisateur puisse obtenir un menu contextuel pour les tâches système, telles que la modification de la résolution de l’écran ou l’obtention des mises à jour logicielles.

 Les notifications au niveau de l’environnement doivent être signalées dans le hub de notifications Visual Studio, et non dans la zone de notification Windows.

#### <a name="notification-bubbles"></a><a name="BKMK_NotificationBubbles"></a> Bulles de notification
 Les bulles de notification peuvent apparaître sous forme d’informations dans un éditeur ou un concepteur ou dans le cadre de la zone de notification Windows. L’utilisateur perçoit ces bulles comme des problèmes qu’ils peuvent résoudre ultérieurement, ce qui constitue un avantage pour les notifications non critiques. Les bulles ne sont pas appropriées pour les informations critiques que l’utilisateur doit résoudre immédiatement. Si vous utilisez des bulles de notification dans Visual Studio, suivez les [conseils Windows Desktop pour les bulles de notification](/windows/desktop/uxguide/mess-notif).

 ![Bulle de notification](../../extensibility/ux-guidelines/media/0901-07_notificationbubbles.png "0901-07_NotificationBubbles")

 **Bulle de notification dans la zone de notification Windows utilisée pour Visual Studio**

## <a name="progress-indicators"></a><a name="BKMK_ProgressIndicators"></a> Indicateurs de progression

### <a name="overview"></a>Vue d’ensemble
 Les indicateurs de progression constituent une partie importante d’un système de notification pour fournir des commentaires à l’utilisateur. Ils indiquent à l’utilisateur quand les processus et les opérations sont terminés. Les types d’indicateur familiers incluent les barres de progression, les curseurs de rotation et les icônes animées. Le type et le positionnement d’un indicateur de progression dépendent du contexte, y compris ce qui est signalé et la durée d’exécution du processus ou de l’opération.

#### <a name="factors"></a>Facteurs
 Pour déterminer le type d’indicateur approprié, vous devez déterminer les facteurs suivants.

1. **Timing :** durée d’exécution de l’opération

2. **Modalité :** indique si l’opération est modale pour l’environnement (verrouille l’interface utilisateur jusqu’à ce que le processus soit terminé)

3. **Persistent/transitoires :** indique si le résultat final de la progression doit être signalé et/ou visible ultérieurement

4. **Determine/Indeterminate :** indique si l’heure de fin et la progression de l’opération peuvent être calculées

5. **Emplacement graphique/textuel :** indique si la progression ou le processus est capturé en ligne, dans le corps d’un message ou dans un contrôle spécifique, tel que le contrôle d’arborescence

6. **Proximite :** indique si la progression doit être à proximité près de l’interface utilisateur à laquelle elle est associée. (Par exemple, peut-il se trouver dans la barre d’État, ce qui peut être éloigné ou doit-il se trouver près du bouton qui a lancé le processus ?)

#### <a name="determinate-progress"></a>Terminer la progression

|Type de progression|Quand et comment utiliser|Remarques|
|-------------------|-------------------------|-----------|
|Barre de progression (arrêt)|Durée attendue de >5 secondes.<br /><br /> Peut inclure une description textuelle des détails du processus.|**N'** incorporez pas de texte dans l’animation.|
|Barre d'informations|Messagerie associée à l’interface utilisateur contextuelle. Consultez [barres](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars).<br /><br /> Peut inclure une description textuelle des détails du processus.|**N’utilisez pas** plusieurs barres quand vous devez indiquer plusieurs processus. Utilisez à la place des barres de progression empilées.|
|Fenêtre Sortie|Notification temporaire : processus au niveau de l’application dont l’utilisateur souhaite **passer en revue** les détails de la fin de l’opération.|**N’utilisez pas** si l’utilisateur doit se référer aux données ultérieurement.|
|Fichier journal|Associé à une notification intransitoire dans les cas où il est important d' **Enregistrer** les détails après l’achèvement.||
|Barre d'état|Notification temporaire : processus au niveau de l’application dont l’utilisateur n’aura **pas besoin** de détails après l’achèvement.<br /><br /> Comprend une barre de progression incorporée.<br /><br /> Peut inclure une description textuelle des détails du processus.||

#### <a name="indeterminate-progress"></a>Progression indéterminée

|Type de progression|Quand et comment utiliser|Remarques|
|-------------------|-------------------------|-----------|
|Barre de progression (indéterminé)|Durée attendue de >5 secondes.<br /><br /> Peut inclure une description textuelle des détails du processus.|**N'** incorporez pas de texte dans l’animation.|
|Ants (points horizontaux animés)|Aller-retour au serveur.<br /><br /> Point près du contexte placé au-dessus du conteneur parent.|**N'** utilisez pas si le parent n’est pas apparenté à l’ensemble du conteneur.|
|Compteur (sonnerie de progression)|Processus associé à une interface utilisateur contextuelle, ou où l’espace est un élément à prendre en compte.<br /><br /> Peut inclure une description textuelle des détails du processus.||
|Barre d'informations|Messagerie associée à l’interface utilisateur contextuelle. Consultez [barres](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars).|**N’utilisez pas** plusieurs barres quand vous devez indiquer plusieurs processus. Utilisez à la place des barres de progression empilées.|
|Fenêtre Sortie|Notification temporaire : processus au niveau de l’application dont l’utilisateur souhaite **passer en revue** les détails de la fin de l’opération.|**N’utilisez pas** pour les informations qui doivent être conservées entre les sessions.|
|Fichier journal|Associé à une notification intransitoire dans les cas où il est important d' **Enregistrer** les détails après l’achèvement.||
|Barre d'état|Notification temporaire : processus au niveau de l’application dont l’utilisateur n’aura **pas besoin** de détails après l’achèvement.<br /><br /> Comprend la barre de progression incorporée.<br /><br /> Peut inclure une description textuelle des détails du processus.||

### <a name="progress-indicator-types"></a>Types d’indicateurs de progression

#### <a name="progress-bars"></a>Barres de progression

##### <a name="indeterminate"></a>Déterminée
 ![Barre de progression indéterminée](../../extensibility/ux-guidelines/media/0901-04_indeterminate.png "0901-04_Indeterminate")

 **Barre de progression indéterminée**

 « Indéterminé » signifie que la progression globale d’une opération ou d’un processus ne peut pas être déterminée. Utilisez des barres de progression indéterminées pour les opérations qui nécessitent une durée illimitée ou qui accèdent à un nombre inconnu d’objets. Utilisez une description textuelle pour accompagner ce qui se passe. Utilisez des délais d’attente pour accorder des limites aux opérations basées sur le temps. Les barres de progression indéterminées utilisent des animations pour montrer que la progression est effectuée, mais ne fournit pas d’autres informations. Ne choisissez pas une barre de progression indéterminée uniquement en fonction du manque de précision possible uniquement.

##### <a name="determinate"></a>Déterminée
 ![Barre de progression de l’arrêt](../../extensibility/ux-guidelines/media/0901-05_determinate.png "0901-05_Determinate")

 **Barre de progression de l’arrêt**

 « Terminate » signifie qu’une opération ou un processus requiert un laps de temps limité, même si cette durée ne peut pas être prédite avec précision. Indiquez clairement la fin de l’opération. Ne laissez pas une barre de progression aller à 100%, sauf si l’opération est terminée. L’animation de la barre de progression de l’arrêt se déplace de gauche à droite de 0 à 100%.

 Ne déplacez jamais l’indicateur de progression vers l’arrière pendant une opération. La barre doit avancer régulièrement lorsque l’opération commence et atteindre 100% lorsqu’elle se termine. Le point de la barre de progression est de permettre à l’utilisateur d’avoir une idée du temps nécessaire à la totalité de l’opération, quel que soit le nombre d’étapes impliquées.

##### <a name="concurrent-reporting-stacked-progress-bars"></a>Rapports simultanés (barres de progression empilées)
 Si une opération prend beaucoup de temps, peut-être plusieurs minutes, puis deux barres de progression peuvent être utilisées, une qui indique la progression globale d’une opération et une autre pour la progression de l’étape actuelle. Par exemple, si un programme d’installation copie de nombreux fichiers, une barre de progression peut être utilisée pour indiquer la durée pendant laquelle l’ensemble du processus prend pendant une seconde peut indiquer le pourcentage du fichier ou du répertoire en cours de copie. Ne signalez pas plus de cinq opérations ou processus simultanés à l’aide des barres de progression empilées. Si vous avez plus de cinq opérations ou processus simultanés à signaler, utilisez une boîte de dialogue modale avec un bouton Annuler et signalez les détails de progression à la Fenêtre Sortie.

##### <a name="textual-descriptions"></a>Descriptions textuelles
 Utilisez une description textuelle pour accompagner ce qui se passe et le délai d’exécution estimé. S’il est impossible de déterminer la durée d’une opération, un meilleur choix pour donner des commentaires peut être une icône animée plutôt qu’une barre de progression.

 Visual Studio fournit une barre de progression standard dans la barre d’État qui peut être utilisée par tout produit intégré à Visual Studio. Pour obtenir des descriptions textuelles de ce qui se passe lorsque la barre de progression est animée, le texte de la barre d’État peut être mis à jour.

#### <a name="other-progress-indicators"></a>Autres indicateurs de progression

##### <a name="ants-animated-horizontal-dots"></a>Ants (points horizontaux animés)
 ![Tirets de progression](../../extensibility/ux-guidelines/media/0903-01_ants.png "0903-01_Ants")

 Les points horizontaux animés « ants » fournissent une référence visuelle pour un processus serveur aller-retour indéterminé.

##### <a name="spinner-progress-ring"></a>Compteur (sonnerie de progression)
 ![Compteur de progression](../../extensibility/ux-guidelines/media/0903-02_spinner.png "0903-02_Spinner")

 Le compteur (également appelé « anneau de progression ») est un indicateur de progression indéterminé utilisé principalement par rapport à l’interface utilisateur contextuelle. Affichez un compteur à proximité du contenu associé, par exemple un en-tête de catégorie textuel, une messagerie ou un contrôle.

##### <a name="cursor-feedback"></a>Commentaires sur le curseur
 Pour les opérations qui prennent entre 2-7 secondes, fournissez des commentaires sur le curseur. En général, cela signifie qu’il faut utiliser le curseur d’attente fourni par le système d’exploitation. Pour obtenir de l’aide, consultez la [propriété de curseurs](/dotnet/api/system.windows.input.cursors.wait)de l’article MSDN. Wait.

#### <a name="progress-indicator-locations"></a>Emplacements des indicateurs de progression

##### <a name="status-bar"></a>Barre d'état
 La barre d’État donne à votre application un emplacement pour afficher des messages et des informations utiles à l’utilisateur sans interrompre le travail de l’utilisateur. Généralement affiché en bas d’une fenêtre, l’état de la progression est un volet d’info-bulle qui contient un message sur la mesure de la progression en association avec un indicateur de barre de progression.

 ![Barre d'état avec barre de progression](../../extensibility/ux-guidelines/media/0903-03_statusbarprogressbar.png "0903-03_StatusBarProgressBar")

 **Barre d'état avec barre de progression**

 ![Barre d'état avec messagerie](../../extensibility/ux-guidelines/media/0903-04_statusbarmessage.png "0903-04_StatusBarMessage")

 **Barre d’État avec description textuelle**

##### <a name="infobar"></a>Barre d'informations
 Comme la barre d’État, la barre d’informations fournit une notification contextuelle et une messagerie, qui peut également être associée à des indicateurs de progression indéterminés tels que la barre de progression ou le compteur. La barre d’informations ne doit pas fournir une indication de progression de niveau granulaire ou de progression de l’arrêt. Consultez [barres](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars).

 ![Barre d'informations avec messagerie et barre de progression](../../extensibility/ux-guidelines/media/0903-05_infobar.png "0903-05_InfoBar")

 **Barre d’informations avec la barre de progression et la description textuelle**

 ![Barre d'informations à l'intérieur d'une fenêtre](../../extensibility/ux-guidelines/media/0903-06_infobarinwindow.png "0903-06_InfoBarInWindow")

##### <a name="inline"></a>En ligne
 L’indication de progression Inline peut être représentée par l’un des types de chargeur de progression. En général, l’indicateur de progression est associé à la messagerie, mais cela n’est pas obligatoire.

 ![Compteur de progression inline](../../extensibility/ux-guidelines/media/0903-07_inlinespinner.png "0903-07_InlineSpinner")

 **Compteur combiné avec une description textuelle**

 ![Barres de progression empilées inline](../../extensibility/ux-guidelines/media/0903-08_inlinestackedprogress.png "0903-08_InlineStackedProgress")

 **Arrêter les barres de progression empilées**

 ![Messagerie de progression inline](../../extensibility/ux-guidelines/media/0903-09_inlinetext.png "0903-09_InlineText")

 **Explorateur de serveurs texte inclus : actualisation...**

##### <a name="tool-windows"></a>Fenêtres d’outil
 L’indication de progression globale est représentée par une barre de progression indéterminée positionnée directement sous la barre d’outils.

 ![Barre de progression indéterminée globale](../../extensibility/ux-guidelines/media/0903-23_globalindeterminate.png "0903-23_GlobalIndeterminate")

 **Team Explorer barre de progression indéterminée globale**

##### <a name="dialogs"></a>Boîtes de dialogue
 Les boîtes de dialogue peuvent contenir n’importe quel type de chargeur de progression. Les indicateurs de progression peuvent être associés à la messagerie et combinés à plusieurs niveaux d’indication de progression pour représenter des sous-processus granulaires.

 ![Boîte de dialogue avec plusieurs types d'indicateurs de progression](../../extensibility/ux-guidelines/media/0903-11_dialog.png "0903-11_Dialog")

 **Boîte de dialogue Visual Studio avec des processus simultanés et plusieurs types d’indicateurs de progression**

 ![Boîte de dialogue avec messagerie et chargeur de progression](../../extensibility/ux-guidelines/media/0903-12_dialog2.png "0903-12_Dialog2")

 **Boîte de dialogue Visual Studio avec chargeur de progression et commandes en ligne de messagerie**

##### <a name="document-well"></a>Barre d’outils document
 La barre d’outils document peut afficher plusieurs types de chargeur de progression en combinaison avec les contrôles.

 ![Messagerie de progression dans une zone de configuration de document](../../extensibility/ux-guidelines/media/0903-13_documentwell.png "0903-13_DocumentWell")

 **Barre de progression indéterminée sous la barre d’outils**

##### <a name="output-window"></a>Fenêtre Sortie
 La fenêtre sortie est appropriée pour gérer la progression du processus et l’état de progression en cours via la messagerie textuelle en ligne. Vous devez utiliser la barre d’État avec les rapports de progression de la fenêtre sortie.

 ![Messagerie de progression dans une fenêtre Sortie](../../extensibility/ux-guidelines/media/0903-14_outputwindow.png "0903-14_OutputWindow")

 **Fenêtre Sortie avec état de processus en cours et messagerie d’attente**

## <a name="infobars"></a><a name="BKMK_Infobars"></a> Barres

### <a name="overview"></a>Vue d’ensemble
 Barres donne à l’utilisateur un indicateur proche de son point d’attention et l’utilisation du contrôle de la barre d’informations partagée garantit la cohérence de l’apparence et de l’interaction visuelle.

 ![Barre](../../extensibility/ux-guidelines/media/0904-01_infobar.png "0904-01_Infobar")

 **Barres dans Visual Studio**

#### <a name="appropriate-uses-for-an-infobar"></a>Utilisations appropriées pour une barre d’informations

- Pour accorder à l’utilisateur un message non bloquant mais important concernant le contexte actuel

- Pour indiquer que l’interface utilisateur est dans un certain État ou condition qui comporte des implications d’interaction, telles que le débogage d’historique

- Pour informer l’utilisateur que le système a détecté des problèmes, par exemple lorsqu’une extension est à l’origine de problèmes de performances

- Pour permettre à l’utilisateur de prendre facilement des mesures, par exemple lorsque l’éditeur détecte qu’un fichier a des onglets et des espaces mélangés

##### <a name="do"></a>À faire :

- Conservez le texte du message de la barre d’informations, bref et jusqu’au point.

- Conservez succinctement le texte sur les liens et les boutons.

- Assurez-vous que les options d’action que vous fournissez aux utilisateurs sont minimes, en n’apparaissant que les actions requises.

##### <a name="dont"></a>Ne pas:

- Utilisez une barre d’informations pour proposer des commandes standard qui doivent être placées dans une barre d’outils.

- Utilisez une barre d’informations à la place d’une boîte de dialogue modale.

- Créez un message flottant en dehors d’une fenêtre.

- Utilisez plusieurs barres à plusieurs emplacements dans la même fenêtre.

#### <a name="can-multiple-infobars-show-at-the-same-time"></a>Plusieurs barres peuvent-ils être affichés en même temps ?
 Oui, plusieurs barres peuvent être affichés en même temps. Elles s’affichent dans l’ordre premier arrivé, premier servi, avec la première barre d’informations affichée en haut et les barres supplémentaires affichées ci-dessous.

 L’utilisateur verra un maximum de trois barres à la fois, après quoi, si davantage de barres sont disponibles, la zone de la barre d’informations deviendra défilant.

### <a name="creating-an-infobar"></a>Création d’une barre d’informations
 La barre d’informations contient quatre sections, de gauche à droite :

- **Icône :** C’est là que vous ajoutez l’icône que vous souhaitez afficher pour la barre d’informations, telle qu’une icône d’avertissement.

- **Texte :** Vous pouvez ajouter du texte pour décrire l’utilisateur du scénario ou de la situation dans, ainsi que des liens dans le texte, si nécessaire. N’oubliez pas de garder le texte concis.

- **Actions :** Cette section doit contenir des liens et des boutons pour les actions que l’utilisateur peut effectuer dans votre barre d’informations.

- **Bouton Fermer :** La dernière section à droite peut avoir un bouton Fermer.

#### <a name="creating-a-standard-infobar-in-managed-code"></a>Création d’une barre d’informations standard dans du code managé
 La classe InfoBarModel peut être utilisée pour créer une source de données pour une barre d’informations. Utilisez l’un de ces quatre constructeurs :

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

#### <a name="creating-a-standard-infobar-in-native-code"></a>Création d’une barre d’informations standard en code natif
 Implémentez l’interface IVsInfoBar pour fournir une barre d’informations à partir du code natif.

```
public interface IVsInfoBar
{
    IVsInfoBarActionItemCollection ActionItems { get; }
    ImageMoniker Image { get; }
    bool IsCloseButtonVisible { get; }
    IVsInfoBarTextSpanCollection TextSpans { get; }
}

```

#### <a name="getting-an-infobar-uielement-from-an-infobar"></a>Obtention d’un UIElement de barre d’informations à partir d’une barre d’informations
 L’implémentation InfoBarModel ou IVsInfoBar sont des modèles de données qui doivent être transformés en UIElement afin d’être affichés dans l’interface utilisateur. Un UIElement peut être récupéré avec le service élément svsinfobaruifactory/IVsInfoBarUIFactory.

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
 Les barres peuvent être affichés à un ou plusieurs des emplacements suivants :

- Fenêtres d’outil

- Dans un onglet de document

> [!IMPORTANT]
> Il est possible de positionner une barre d’informations pour envoyer un message sur le contexte global. Cela s’affiche entre les barres d’outils et le document. Cela n’est pas recommandé, car cela entraîne des problèmes avec le « saut et le saccadé » de l’IDE et doit être évité, sauf nécessité absolue et appropriée.

#### <a name="placing-an-infobar-in-a-toolwindowpane"></a>Placement d’une barre d’informations dans un ToolWindowPane
 La méthode ToolWindowPane. AddInfoBar (IVsInfoBar) peut être utilisée pour ajouter une barre d’informations à une fenêtre outil. Cette API peut soit ajouter un IVsInfoBar (dont InfoBarModel est une implémentation par défaut), soit un IVsUIElement.

#### <a name="placing-an-infobar-in-a-document-or-non-toolwindowpane"></a>Placement d’une barre d’informations dans un document ou non ToolWindowPane
 Pour placer une barre d’informations dans un IVsWindowFrame, utilisez la propriété VSFPROPID_InfoBarHost pour obtenir le IVsInfoBarHost du frame, puis ajoutez le UIElement de la barre d’informations.

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

#### <a name="placing-an-infobar-in-the-main-window"></a>Placement d’une barre d’informations dans la fenêtre principale
 Pour placer une barre d’informations dans la fenêtre principale, utilisez la VSSPROPID_MainWindowInfoBarHost du service IVsShell pour récupérer la IVsInfoBarHost de la fenêtre principale, puis ajoutez la barre d’informations UIElement à celle-ci.

### <a name="will-i-know-when-the-user-takes-action-in-my-infobar"></a>Est-ce que je sais quand l’utilisateur effectue une action dans ma barre d’informations ?
 Oui, nous retournerons chaque action d’événement à l’auteur de la barre d’informations. Il revient ensuite à l’auteur de la barre d’informations d’agir dans l’IDE en fonction de la sélection de l’utilisateur dans la barre d’informations. Barres sera automatiquement supprimé de l’hôte dont l’utilisateur a cliqué sur le bouton Fermer, mais un travail supplémentaire est nécessaire si d’autres barres doivent être supprimés après la fermeture. Les données de télémétrie devront également être journalisées indépendamment par chaque barre d’informations.

#### <a name="receiving-infobar-events-in-a-toolwindowpane"></a>Réception d’événements de barre d’informations dans un ToolWindowPane
 ToolWindowPane a deux événements pour barres. L’événement InfoBarClosed est déclenché quand une barre d’informations dans le ToolWindowPane est fermée. L’événement InfoBarActionItemClicked est déclenché lorsqu’un clic est effectué sur un lien hypertexte ou un bouton à l’intérieur de la barre d’informations.

#### <a name="receiving-infobar-events-directly-from-the-uielement"></a>Réception d’événements de barre d’informations directement à partir de l’UIElement
 IVsInfoBarUIElement. Advise peut être utilisé pour s’abonner à des événements directement à partir du UIElement d’une barre d’informations. L’implémentation de IVsInfoBarUIEvents permet à l’auteur de recevoir des événements de fermeture et de clic.

```
public interface IVsInfoBarUIEvents
{
    void OnActionItemClicked(IVsInfoBarUIElement infoBarUIElement, IVsInfoBarActionItem actionItem);
    void OnClosed(IVsInfoBarUIElement infoBarUIElement);
}

```

## <a name="error-validation"></a><a name="BKMK_ErrorValidation"></a> Validation des erreurs
 Lorsqu’un utilisateur entre des informations qui ne sont pas acceptables, par exemple lorsqu’un champ obligatoire est ignoré ou lorsque les données sont entrées dans un format incorrect, il est préférable d’utiliser la validation de contrôle ou les commentaires près du contrôle au lieu d’utiliser une boîte de dialogue d’erreur contextuelle de blocage.

### <a name="field-validation"></a>Validation du champ
 La validation de formulaire et de champ est constituée de trois composants : un contrôle, une icône et une info-bulle. Bien que plusieurs types de contrôles puissent l’utiliser, une zone de texte est utilisée à titre d’exemple.

 ![Validation de champ &#40;&#41;vide ](../../extensibility/ux-guidelines/media/0905-01_fieldvalidation.png "0905-01_FieldValidation")

 Si le champ est obligatoire, il doit y avoir un texte **\<Required>** de filigrane indiquant et l’arrière-plan du champ doit être en jaune clair (VSColor : `Environment.ControlEditRequiredBackground` ) et le premier plan doit être gris (VSColor : `Environment.ControlEditRequiredHintText` ) :

 ![Validation de champ avec étiquette « Obligatoire »](../../extensibility/ux-guidelines/media/0905-02_fieldvalidationrequired.png "0905-02_FieldValidationRequired")

 Le programme peut déterminer que le contrôle est dans un état de *contenu non valide entré* lorsque le focus est déplacé vers un autre contrôle ou lorsque l’utilisateur clique sur un bouton de validation [OK] ou lorsque l’utilisateur enregistre le document ou le formulaire.

 Lorsque l’état de contenu non valide est déterminé, une icône s’affiche à l’intérieur du contrôle ou juste en regard de celle-ci. Une info-bulle décrivant l’erreur doit s’afficher au pointage de l’icône ou du contrôle. En outre, une bordure de 1 pixel doit apparaître autour du contrôle qui crée l’état non valide.

 ![Spécifications de disposition de validation de champ](../../extensibility/ux-guidelines/media/0905-03_layoutspecs.png "0905-03_LayoutSpecs")

 **Spécifications de disposition pour la validation de champ**

#### <a name="acceptable-variations-for-icon-location"></a>Variations acceptables de l’emplacement de l’icône
 Dans certains cas, les utilisateurs doivent être informés des erreurs de validation. En tenant compte du type de contrôle et de la configuration de l’interface utilisateur, choisissez l’emplacement des icônes approprié à votre situation.

 ![Emplacements acceptables pour l'emplacement de l'icône](../../extensibility/ux-guidelines/media/0905-04_iconlocation.png "0905-04_IconLocation")

 **Variations acceptables pour les emplacements d’icône de validation de champ**

#### <a name="validation-requiring-a-round-trip-to-a-server-or-network-connection"></a>Validation nécessitant un aller-retour vers un serveur ou une connexion réseau
 Dans certains cas, un aller-retour au serveur est nécessaire pour vérifier le contenu, et il est important de montrer les États de progression, de vérification et d’erreur de l’utilisateur. La figure ci-dessous montre un exemple de ce cas et de l’interface utilisateur recommandée.

 ![Validation impliquant un aller-retour vers un serveur](../../extensibility/ux-guidelines/media/0905-05_roundtrip.png "0905-05_RoundTrip")

 **Validation impliquant un aller-retour vers un serveur**

 Notez que l’espace disponible approprié à droite du contrôle doit être fourni afin de prendre en charge la vérification... et le texte « réessayer ».

#### <a name="in-place-warning-text"></a>Texte d’avertissement sur place
 Lorsqu’il y a de l’espace disponible pour mettre le message d’erreur près du contrôle dans un état d’erreur, il est préférable d’utiliser l’info-bulle seule.

 ![Avertissement en&#45;place](../../extensibility/ux-guidelines/media/0905-06_inplacewarning.png "0905-06_InPlaceWarning")

 **Texte d’avertissement sur place**

#### <a name="watermarks"></a>Filigranes
 Parfois, l’intégralité d’un contrôle ou d’une fenêtre est dans un état d’erreur. Dans ce cas, utilisez un filigrane pour indiquer l’erreur.

 ![Portent](../../extensibility/ux-guidelines/media/0905-07_watermark.png "0905-07_Watermark")

 **Validation du champ de filigrane**
