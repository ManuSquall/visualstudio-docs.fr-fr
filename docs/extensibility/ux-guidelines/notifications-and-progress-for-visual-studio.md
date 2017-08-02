---
title: Notifications et progression pour Visual Studio | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f0ef65e9-0f1f-45f4-9f25-6e2398691168
caps.latest.revision: 6
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 1f7823754601161200edafdce998ebe9aeab2723
ms.lasthandoff: 02/22/2017

---
# <a name="notifications-and-progress-for-visual-studio"></a>Notifications et progression pour Visual Studio
##  <a name="a-namebkmknotificationsystemsa-notification-systems"></a><a name="BKMK_NotificationSystems"></a>Systèmes de notification  
  
### <a name="overview"></a>Vue d'ensemble  
 Il existe plusieurs façons pour informer l’utilisateur de ce qui se passe dans Visual Studio en ce qui concerne leurs tâches de développement logiciel.  
  
 Lors de l’implémentation de n’importe quel type de notification :  
  
-   **Limiter le nombre de notifications au minimum** nombre effectif. Messages de notification doivent s’appliquer à la majorité des utilisateurs de Visual Studio ou à des utilisateurs d’une zone de fonctionnalité ou une fonctionnalité spécifique. Une utilisation excessive des notifications sidetrack de l’utilisateur ou diminuer perçue facilité d’utilisation du système.  
  
-   **Vérifiez vous présentez des messages claires et concret** que l’utilisateur peut utiliser pour appeler le contexte approprié pour faire des choix plus complexes et entreprendre d’action supplémentaire.  
  
-   **Présenter correctement les messages synchrones et asynchrones.** Notifications synchrone indiquent que quelque chose nécessite une intervention immédiate, par exemple lorsqu’un service web tombe en panne ou un code d’exception est levée. L’utilisateur doit être informé de ces situations immédiatement d’une manière qui nécessite son intervention, comme dans une boîte de dialogue modale. Les notifications asynchrones sont ceux que l’utilisateur doit connaître mais ne pas obligatoirement agir immédiatement, comme à l’issue de l’exécution d’une opération de génération ou d’un site web s’achève. Ces messages doivent être plus ambiante et interrompt pas le flux de tâches de l’utilisateur.  
  
-   **Utilisez les boîtes de dialogue modales uniquement lorsque cela est nécessaire pour empêcher l’utilisateur de passer outre** avant d’accuser réception du message ou d’une décision présentées dans la boîte de dialogue.  
  
-   **Supprimer les notifications ambiantes lorsqu’ils ne sont plus valides.** Ne nécessitent pas l’utilisateur ferme une notification si elles ont déjà pris des mesures pour résoudre le problème, qu'ils ont été avertis.  
  
-   **N’oubliez pas que les notifications peuvent entraîner des corrélations false.** Les utilisateurs peuvent penser qu’une ou plusieurs de leurs actions a déclenché une notification qu’il y a en fait aucune relation causale. Être clairement dans le message de notification sur le contexte, le déclencheur et la source de la notification.  
  
### <a name="choosing-the-right-method"></a>Choisir le bon procédé  
 Utilisez cette table pour vous aider à choisir la bonne méthode pour informer l’utilisateur de votre message.  
  
|Méthode|Utilisation|N’utilisez pas|  
|------------|---------|----------------|  
|[Boîtes de dialogue de message erreur modal](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ModalErrorMessageDialogs)|À utiliser lors de la réponse d’un utilisateur est nécessaire avant de continuer.|N’utilisez pas lorsqu’il n’est pas nécessaire à l’utilisateur et leur flux à interrompre. Évitez d’utiliser les boîtes de dialogue modales s’il est possible d’afficher un message d’une autre manière moins intrusif.|  
|[Barre d’état IDE](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_IDEStatusBar)|À utiliser lorsque des informations textuelles ambiantes concernant l’état d’un processus.|N’utilisez pas seul. Mieux utilisée conjointement avec un autre mécanisme de commentaires.|  
|[Barre d’informations incorporée](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_EmbeddedInfobar)|Dans une fenêtre outil ou une fenêtre de document, utilisez pour informer de progression, résultats d’état d’erreur et/ou des informations utilisables.|N’utilisez pas si les informations sont applique pas à l’emplacement où se trouve la barre d’informations.<br /><br /> N’utilisez pas hors d’une fenêtre de document et d’outils.|  
|[Modifications de curseur de souris](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_MouseCursorChanges)|Peut être utilisé pour notifier qu’un processus se. Également utilisé pour signaler qu’un changement d’état de la souris, tels que lors de l’opération glisser-déplacer est en cours ou que le pointeur se trouve dans un certain mode, telles que le mode de dessin.|N’utilisez pas les modifications de progression court ou si un mot de curseur est probablement (par exemple, lorsque liée à des parties d’un processus en cours d’exécution plus longs à la place de l’ensemble du processus).|  
|[Indicateurs de progression](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_NotSysProgressIndicators)|À utiliser lorsque vous devez signaler la progression (déterminé ou indéterminé). Il existe une variété de types d’indicateurs de progression et d’utilisation spécifiques pour chaque. Consultez la page [les indicateurs de progression](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ProgressIndicators).||  
|[Fenêtre de Visual Studio Notifications](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_VSNotificationsToolWindow)|La fenêtre Notifications n’est pas extensible publiquement. Toutefois, il est utilisé pour communiquer une plage de messages sur Visual Studio, y compris les problèmes critiques avec votre licence et des notifications d’information des mises à jour pour Visual Studio ou à des packages.|N’utilisez pas pour d’autres types de notifications.|  
|[Liste d’erreurs](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ErrorList)|Lorsque le problème est lié directement à la solution actuellement ouverte à l’utilisateur ayant un problème (erreur/avertissement / d’informations), ils devront peut-être effectuer une opération sur le code.<br /><br /> Cela inclut, par exemple :<br /><br /> -Messages du compilateur (erreur/avertissement / d’informations)<br /><br /> -Messages d’analyseur de Diagnostic code sur le code<br /><br /> -Générer des messages<br /><br /> Peut être appropriée pour les problèmes liés aux fichiers projet ou solution, mais envisagez d’abord une indication de l’Explorateur de solutions.|N’utilisez pas pour les éléments qui n’ont pas aucun rapport avec le code de l’utilisateur ouvrir une solution.|  
|Notifications de l’éditeur : ampoule|À utiliser lorsque vous avez un correctif disponible pour résoudre un problème qui existe dans le fichier ouvert.<br /><br /> Ampoule doit également être utilisée pour l’hébergement des Actions rapides qui sont effectuées sur le code de l’utilisateur à la demande, telles que des refactorisations, mais dans ce cas, n’apparaissent pas « style de notification ».|N’utilisez pas pour les éléments qui n’ont pas de n’importe quelle relation vers le fichier ouvert.|  
|Notifications de l’éditeur : soulignements ondulés|Utiliser pour avertir l’utilisateur d’un problème avec une étendue particulière de leur code ouvert (par exemple, une ligne ondulée rouge pour les erreurs).|N’utilisez pas pour les éléments qui ne sont pas liées à une plage particulière de leur code ouvert.|  
|[Barres d’état incorporée](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_EmbeddedStatusBars)|Permet de fournir l’état lié au contenu ou processus dans le contexte d’une fenêtre outil spécifique, la fenêtre de document ou la fenêtre de la boîte de dialogue.|N’utilisez pas de notifications de produit, des processus ou des éléments qui n’ont pas aucun rapport avec le contenu dans la fenêtre spécifique.|  
|[Notifications de barre d’état système Windows](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_WindowsTray)|Utilisez à la surface des notifications pour les processus out-of-process ou le Guide des applications.|N’utilisez pas pour les notifications qui sont pertinentes pour l’IDE.|  
|[Bulles de notification](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_NotificationBubbles)|Permet de notifier d’un processus à distance ou modifier **hors** de l’IDE.|N’utilisez pas comme un moyen pour avertir l’utilisateur du processus **dans** l’IDE.|  
  
### <a name="notification-methods"></a>Méthodes de notification  
  
####  <a name="a-namebkmkmodalerrormessagedialogsa-modal-error-message-dialogs"></a><a name="BKMK_ModalErrorMessageDialogs"></a>Boîtes de dialogue de message erreur modal  
 Boîte de message d’erreur modal est utilisée pour afficher un message d’erreur qui requiert une confirmation ou action de l’utilisateur.  
  
 ![Message d’erreur modal](~/extensibility/ux-guidelines/media/0901-01_modalerrormessage.png "01_ModalErrorMessage-0901")  
  
 **Une boîte de dialogue modale erreur message avertissant l’utilisateur d’une chaîne de connexion non valide à une base de données**  
  
####  <a name="a-namebkmkidestatusbara-ide-status-bar"></a><a name="BKMK_IDEStatusBar"></a>Barre d’état IDE  
 La probabilité que les utilisateurs aperçoivent texte barre d’état correspond à leur expérience ultra-rapide et l’expérience spécifique à la plate-forme Windows. La base de clients Visual Studio a tendance à être expérimentés dans les deux domaines, bien que même compétentes Windows les utilisateurs peuvent passer les modifications dans la barre d’état. Par conséquent, la barre d’état est utilisée à titre d’information ou comme une file d’attente redondante pour les informations présentées ailleurs. Tout type d’informations importantes dont l’utilisateur doit résoudre immédiatement doit être fournie dans une boîte de dialogue ou dans la fenêtre d’outil des Notifications.  
  
 La barre d’état de Visual Studio est conçue pour permettre plusieurs types d’informations à afficher. Il est divisé en régions pour les commentaires, le concepteur, barre de progression, l’animation et client.  
  
 La zone de commentaires et de la zone du concepteur sont toujours visibles. La barre de progression et l’animation sont toujours des régions dynamique et repose sur le contexte de l’utilisateur. La zone du concepteur a une largeur statique déterminée par la longueur de la chaîne est extraite à partir d’une ressource pour le message de texte qui accompagne cet article. Cela permet de localisation de redimensionner la largeur sans nécessiter une modification du code. Pour l’anglais, la largeur de cette chaîne est environ 220 pixels. La zone du concepteur se comporte normalement et que la zone de commentaires absorbe l’espace restant.  
  
 La barre d’état est également colorée pour ajouter un intérêt visuel et valeur fonctionnelle en communiquant différents changements d’état IDE tel que lorsque l’IDE est en mode débogage.  
  
 ![Les modifications de couleur de la barre d’état IDE](~/extensibility/ux-guidelines/media/0901-02_idestatusbar.png "02_IDEStatusBar-0901")  
  
 **Couleurs de barre d’état IDE**  
  
####  <a name="a-namebkmkembeddedinfobara-embedded-infobar"></a><a name="BKMK_EmbeddedInfobar"></a>Barre d’informations incorporée  
 Une barre d’informations peut servir à informer l’utilisateur d’un état ou une condition en haut d’une fenêtre de document ou d’une fenêtre outil. Il peut également offrir des commandes afin que l’utilisateur peut avoir un moyen de tirer facilement action. La barre d’informations est un contrôle d’interface standard. Évitez de créer votre propre, qui agissent et semblent incohérent avec d’autres utilisateurs dans l’IDE. Consultez la page [barres](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars) pour des détails d’implémentation et le Guide d’utilisation.  
  
 ![Embedded barre d’informations](~/extensibility/ux-guidelines/media/0901-03_embeddedinfobar.png "03_EmbeddedInfobar-0901")  
  
 **Une barre d’informations incorporées dans une fenêtre de document, avertissant l’utilisateur que l’IDE est en mode débogage d’historique et l’éditeur ne répondra pas de la même façon que le mode débogage standard.**  
  
####  <a name="a-namebkmkmousecursorchangesa-mouse-cursor-changes"></a><a name="BKMK_MouseCursorChanges"></a>Modifications de curseur de souris  
 Lorsque vous modifiez le curseur de souris, utiliser des couleurs qui sont liés au service VSColor et sont déjà associés avec le curseur. Curseur se transforme en peut être utilisé pour indiquer une opération en cours, ainsi que les zones où l’utilisateur pointe sur une cible qui peut être déplacée, déposée ou permet de sélectionner un objet d’accès.  
  
 Utilisez le curseur occupé/attente uniquement lorsque tout le temps processeur disponible doit être réservé pour une opération, ce qui empêche l’utilisateur à partir de l’expression d’entrée supplémentaire. Dans la plupart des cas avec des applications bien écrites à l’aide du multithreading, les heures lorsque les utilisateurs ne peuvent pas effectuer d’autres opérations doivent être rares.  
  
 N’oubliez pas que le curseur se transforme est utiles comme une file d’attente redondant pour plus d’informations présentées ailleurs. Ne comptez pas sur un changement de curseur comme seul moyen de communiquer avec l’utilisateur, en particulier lorsque vous essayez de faire passer un élément essentiel que l’utilisateur doit résoudre.  
  
####  <a name="a-namebkmknotsysprogressindicatorsa-progress-indicators"></a><a name="BKMK_NotSysProgressIndicators"></a>Indicateurs de progression  
 Indicateurs de progression sont importants pour les commentaires utilisateur pendant les processus qui prennent plus de quelques secondes. Indicateurs de progression peuvent être affichées en place (à côté du point de lancement de l’action en cours), dans la barre d’état incorporée, dans une boîte de dialogue modale ou dans la barre d’état de Visual Studio. Suivez les instructions de [les indicateurs de progression](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ProgressIndicators) concernant leur utilisation et l’implémentation.  
  
####  <a name="a-namebkmkvsnotificationstoolwindowa-visual-studio-notifications-window"></a><a name="BKMK_VSNotificationsToolWindow"></a>Fenêtre de Visual Studio Notifications  
 La fenêtre Notifications de Visual Studio notifie les développeurs sur les licences, environnement (Visual Studio), extensions et mises à jour. Les utilisateurs peuvent fermer des notifications individuelles ou peuvent choisir d’ignorer certains types de notifications. La liste des notifications ignorées est gérée dans un **Outils > Options** page.  
  
 La fenêtre Notifications n’est pas actuellement extensible.  
  
 ![Fenêtre de Visual Studio Notifications](~/extensibility/ux-guidelines/media/0901-06_vsnotificationswindow.png "06_VSNotificationsWindow-0901")  
  
 **Fenêtre de Visual Studio Notifications outil**  
  
####  <a name="a-namebkmkerrorlista-error-list"></a><a name="BKMK_ErrorList"></a>Liste d’erreurs  
 Une notification dans la liste d’erreurs indiquent des erreurs et avertissements qui s’est produite lors de la compilation et de processus de génération et permettant à l’utilisateur de naviguer dans le code de cette erreur de code spécifique.  
  
 ![Liste d’erreurs](~/extensibility/ux-guidelines/media/0901-08_errorlist.png "08_ErrorList-0901")  
  
 **Liste d’erreurs dans Visual Studio**  
  
####  <a name="a-namebkmkembeddedstatusbarsa-embedded-status-bars"></a><a name="BKMK_EmbeddedStatusBars"></a>Barres d’état incorporée  
 La barre d’état IDE étant dynamique, avec son contexte de région client défini dans la fenêtre de document actif et de la mise à jour sur le contexte de l’utilisateur et/ou les réponses du système d’informations, il est difficile de maintenir un affichage d’informations en continu ou donner un état de processus asynchrones à long terme. Par exemple, la barre d’état IDE n’est pas appropriée pour les notifications de résultats de la série de tests pour plusieurs séries et/ou les sélections d’élément immédiatement exploitable. Il est important de conserver ces informations d’état dans le contexte de la fenêtre de document ou l’outil où l’utilisateur effectue une sélection ou démarre un processus.  
  
 ![Barre d’état incorporée](~/extensibility/ux-guidelines/media/0901-09_embeddedstatusbar.png "09_EmbeddedStatusBar-0901")  
  
 **Barre d’état incorporée dans Visual Studio**  
  
####  <a name="a-namebkmkwindowstraya-windows-tray-notifications"></a><a name="BKMK_WindowsTray"></a>Notifications de barre d’état système Windows  
 La zone de notification se trouve à côté du système de Windows de l’horloge dans la barre des tâches Windows. De nombreux utilitaires et composants logiciels fournissent des icônes de cette zone afin que l’utilisateur peut obtenir un menu contextuel pour les tâches système, telles que la modification de la résolution d’écran ou d’obtenir des mises à jour logicielles.  
  
 Notifications de niveau de l’environnement doivent être signalées dans le concentrateur de Notifications de Visual Studio, pas la zone de notification Windows.  
  
####  <a name="a-namebkmknotificationbubblesa-notification-bubbles"></a><a name="BKMK_NotificationBubbles"></a>Bulles de notification  
 Les bulles de notification peuvent apparaître à titre d’information au sein d’un éditeur/concepteur ou dans le cadre de la zone de Notification Windows. L’utilisateur perçoit ces bulles comme problèmes qu’ils peuvent résoudre plus tard, qui est un avantage pour les notifications non critiques. Les bulles sont inappropriés pour que l’utilisateur doit résoudre immédiatement les informations critiques. Si vous utilisez des bulles de notification dans Visual Studio, suivez les [des conseils de bureau Windows pour les bulles de notification](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742472\(v=vs.85\).aspx).  
  
 ![Bulle de notification](~/extensibility/ux-guidelines/media/0901-07_notificationbubbles.png "07_NotificationBubbles-0901")  
  
 **Bulle de notification dans la zone de Notification Windows utilisée pour Visual Studio**  
  
##  <a name="a-namebkmkprogressindicatorsa-progress-indicators"></a><a name="BKMK_ProgressIndicators"></a>Indicateurs de progression  
  
### <a name="overview"></a>Vue d'ensemble  
 Les indicateurs de progression sont une partie importante d’un système de notification pour les commentaires de l’utilisateur. Ils indiquent l’utilisateur lorsque le processus et des opérations seront achève. Types d’indicateurs familier incluent les barres de progression, les curseurs de rotation et icônes animées. Le type et l’emplacement d’un indicateur de progression varie selon le contexte, y compris les données consignées et la durée pendant laquelle le processus ou une opération se pour terminer.  
  
#### <a name="factors"></a>Facteurs  
 Afin de déterminer quel type d’indicateur est approprié, vous devez déterminer les facteurs suivants.  
  
1.  **Minutage :** prendra de temps l’opération  
  
2.  **Modalité :** si l’opération est modale pour l’environnement (verrou de l’interface utilisateur jusqu'à ce que le processus est terminé)  
  
3.  **Permanent/temporaire :** si le résultat final de la progression doit être signalée et/ou visible ultérieurement  
  
4.  **Déterminée/Indeterminate :** si l’heure de fin d’opération et la progression peuvent être calculées  
  
5.  **Emplacement d’image/texte :** indique si la progression ou le processus est capturée inline, dans le corps d’un message ou un contrôle spécifique, tel que le contrôle d’arborescence  
  
6.  **Proximité :** indique si la progression doit être à proximité de l’interface utilisateur qui lui sont associés. (Par exemple, peut être dans la barre d’état, ce qui peut être éloigné, ou qu’il ne doit rester à proximité du bouton qui a lancé le processus ?)  
  
#### <a name="determinate-progress"></a>Progression déterminée  
  
|Type de cours|Quand et comment utiliser|Notes|  
|-------------------|-------------------------|-----------|  
|Barre de progression (déterminée)|Durée d’attendue >&5; secondes.<br /><br /> Peut inclure une description textuelle des détails du processus.|**Ne pas** incorporez du texte dans l’animation.|  
|Barre d'informations|Messagerie associé à l’interface utilisateur contextuelle. Consultez la page [barres](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars).<br /><br /> Peut inclure une description textuelle des détails du processus.|**Ne pas** utiliser plusieurs barres lorsque vous avez besoin indiquer plusieurs processus. Utilisez à la place des barres de progression empilées.|  
|Fenêtre Sortie|Notification temporaire : processus au niveau de l’application utilisateur souhaitez **Examinez** détails d’après l’achèvement.|**Ne pas** utiliser si l’utilisateur doit faire référence aux données ultérieurement.|  
|Fichier journal|Associé à la notification intransient dans le cas lorsqu’il est important de **enregistrer** détails après l’achèvement.||  
|Barre d'état|Notification temporaire : processus au niveau de l’application que l’utilisateur sera **inutile** détails d’après l’achèvement.<br /><br /> Inclut une barre de progression incorporé.<br /><br /> Peut inclure une description textuelle des détails du processus.||  
  
#### <a name="indeterminate-progress"></a>Progression indéterminée  
  
|Type de cours|Quand et comment utiliser|Notes|  
|-------------------|-------------------------|-----------|  
|Barre de progression (indéterminé)|Durée d’attendue >&5; secondes.<br /><br /> Peut inclure une description textuelle des détails du processus.|**Ne pas** incorporez du texte dans l’animation.|  
|ANTS (points animés horizontales)|Aller-retour au serveur.<br /><br /> Placés près du point du contexte entre le haut du conteneur parent.|**Ne pas** utiliser si non apparenté à l’intégralité du conteneur.|  
|Spinner (boucle de progression)|Processus associée à l’interface utilisateur contextuel, où l’espace est un facteur important.<br /><br /> Peut inclure une description textuelle des détails du processus.||  
|Barre d'informations|Messagerie associé à l’interface utilisateur contextuelle. Consultez la page [barres](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars).|**Ne pas** utiliser plusieurs barres lorsque vous avez besoin indiquer plusieurs processus. Utilisez à la place des barres de progression empilées.|  
|Fenêtre Sortie|Notification temporaire : processus au niveau de l’application utilisateur souhaitez **Examinez** détails d’après l’achèvement.|**Ne pas** pour les informations devant être conservées entre les sessions.|  
|Fichier journal|Associé à la notification intransient dans le cas lorsqu’il est important de **enregistrer** détails après l’achèvement.||  
|Barre d'état|Notification temporaire : processus au niveau de l’application que l’utilisateur sera **inutile** détails d’après l’achèvement.<br /><br /> Inclut la barre de progression incorporé.<br /><br /> Peut inclure une description textuelle des détails du processus.||  
  
### <a name="progress-indicator-types"></a>Types d’indicateurs de progression  
  
#### <a name="progress-bars"></a>Barres de progression  
  
##### <a name="indeterminate"></a>Indéterminé  
 ![Barre de progression indéterminée](~/extensibility/ux-guidelines/media/0901-04_indeterminate.png "04_Indeterminate-0901")  
  
 **Barre de progression indéterminée**  
  
 « Indéterminé » signifie que la progression globale d’une opération ou le processus ne peut pas être déterminé. Utilisez les barres de progression indéterminée pour les opérations qui requièrent un nombre illimité de fois ou qui accèdent à un nombre inconnu d’objets. Utilisez une description textuelle pour accompagner ce qui se passe. Utiliser des délais d’attente pour permettre à des limites aux opérations basées sur le temps. Barres de progression indéterminée utilisent des animations pour montrer que progression est en cours, mais fournissent pas d’autres informations. Ne choisissez pas une barre de progression indéterminée basée uniquement sur le manque de précision seul possible.  
  
##### <a name="determinate"></a>Déterminée  
 ![Barre de progression déterminée](~/extensibility/ux-guidelines/media/0901-05_determinate.png "05_Determinate-0901")  
  
 **Barre de progression déterminée**  
  
 « Déterminée » signifie qu’une opération ou un processus nécessite une durée limitée, même si ce laps de temps ne peut pas être prédites avec précision. Indique clairement l’achèvement. Ne laissez pas une barre de progression atteindre 100 pour cent, sauf si l’opération est terminée. Animation de barre de progression déterminée déplace de gauche à droite de 0 à 100 %.  
  
 L’indicateur de progression vers l’arrière pendant une opération ne changera jamais. La barre doit avancer régulièrement lorsque l’opération commence et atteindre 100 % lorsqu’elle se termine. Le point de la barre de progression est à l’utilisateur une idée de la durée pendant laquelle l’opération entière prend, quel que soit le nombre d’étapes impliqué.  
  
##### <a name="concurrent-reporting-stacked-progress-bars"></a>Simultanées reporting (barres de progression empilées)  
 Si une opération prendra un certain temps – éventuellement plusieurs minutes – deux barres peuvent être utilisé, un qui affiche la progression globale d’une opération et l’autre pour la progression de l’étape en cours. Par exemple, si un programme d’installation copie de fichiers, une barre de progression peut être utilisé pour indiquer la durée pendant laquelle l’intégralité du processus prend alors que la seconde peut indiquer quel pourcentage du fichier ou répertoire est copié. Ne signalent pas plus de cinq opérations simultanées ou des processus à l’aide des barres de progression empilées. Si vous avez plus de cinq opérations simultanées ou des processus pour le rapport, utilisez une boîte de dialogue modale avec un rapport et un bouton Annuler les détails de la progression dans la fenêtre Sortie.  
  
##### <a name="textual-descriptions"></a>Descriptions textuelles  
 Utilisez une description textuelle pour accompagner ce qui se passe et l’heure de fin estimée. S’il est impossible de déterminer la durée pendant laquelle une opération dure, un meilleur choix pour l’apport de commentaires peut être une icône animée plutôt qu’une barre de progression.  
  
 Visual Studio fournit une barre de progression dans la barre d’état qui peut être utilisée par tous les produits intégrés à Visual Studio. Pour obtenir une description textuelle de ce qui se passe alors que la barre de progression, vous pouvez mettre à jour le texte de la barre d’état.  
  
#### <a name="other-progress-indicators"></a>Autres indicateurs de progression  
  
##### <a name="ants-animated-horizontal-dots"></a>ANTS (points animés horizontales)  
 ![Tirets de progression](~/extensibility/ux-guidelines/media/0903-01_ants.png "0903-01_Ants")  
  
 « Fourmis, » points horizontales animés, fournissent une référence visuelle d’un processus serveur aller-retour indéterminé.  
  
##### <a name="spinner-progress-ring"></a>Spinner (boucle de progression)  
 ![Compteur de progression](~/extensibility/ux-guidelines/media/0903-02_spinner.png "0903-02_Spinner")  
  
 La zone de sélection numérique (également appelé une « boucle de progression ») est un indicateur de progression indéterminée principalement utilisé par rapport à l’interface utilisateur contextuelle. Afficher un compteur à proximité de son contenu associé, comme un en-tête de catégorie de texte, de messagerie ou un contrôle.  
  
##### <a name="cursor-feedback"></a>Curseur  
 Pour les opérations qui prennent entre 2 à 7 secondes, fournir des commentaires de curseur. En règle générale, cela signifie à l’aide du curseur d’attente fourni par le système d’exploitation. Pour obtenir des instructions, consultez l’article MSDN [Cursors.Wait propriété](https://msdn.microsoft.com/en-us/library/system.windows.input.cursors.wait\(v=vs.110\).aspx).  
  
#### <a name="progress-indicator-locations"></a>Emplacements d’indicateur de progression  
  
##### <a name="status-bar"></a>Barre d'état  
 La barre d’état permet à votre application à afficher des messages et des informations utiles à l’utilisateur sans interrompre le travail de l’utilisateur. Généralement affiché au bas d’une fenêtre, l’état de progression sera un volet d’outils de pointe qui contient un message concernant la mesure de la progression en association avec un indicateur de barre de progression.  
  
 ![Barre d’état avec barre de progression](~/extensibility/ux-guidelines/media/0903-03_statusbarprogressbar.png "0903-03_StatusBarProgressBar")  
  
 **Barre d’état avec barre de progression**  
  
 ![Barre d’état avec messagerie](~/extensibility/ux-guidelines/media/0903-04_statusbarmessage.png "0903-04_StatusBarMessage")  
  
 **Barre d’état avec le texte de description**  
  
##### <a name="infobar"></a>Barre d'informations  
 Similaire à la barre d’état, la barre d’informations fournit des notifications contextuelles et messagerie, qui peut également être associé aux indicateurs de progression indéterminée telles que la barre de progression ou le compteur. La barre d’informations ne doit pas fournir de progression au niveau granulaire ou une indication de progression déterminée. Consultez la page [barres](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars).  
  
 ![Barre d’informations avec messagerie et de la barre de progression](~/extensibility/ux-guidelines/media/0903-05_infobar.png "0903-05_InfoBar")  
  
 **Barre d’informations avec la barre de progression et une description textuelle**  
  
 ![Barre d’informations à l’intérieur d’une fenêtre](~/extensibility/ux-guidelines/media/0903-06_infobarinwindow.png "0903-06_InfoBarInWindow")  
  
 **Barre d’informations à l’intérieur de la fenêtre d’analyse du Code**  
  
##### <a name="inline"></a>Inline  
 Indication de progression inline peut être représentée par les types de chargeur de progression. L’indicateur de progression est généralement combinée avec la messagerie, mais ce n’est pas obligatoire.  
  
 ![Compteur de progression inline](~/extensibility/ux-guidelines/media/0903-07_inlinespinner.png "0903-07_InlineSpinner")  
  
 **Combiné avec une description textuelle de compteur**  
  
 ![Barres de progression empilées inline](~/extensibility/ux-guidelines/media/0903-08_inlinestackedprogress.png "0903-08_InlineStackedProgress")  
  
 **Barres de progression empilées déterminée**  
  
 ![Messagerie de progression inline](~/extensibility/ux-guidelines/media/0903-09_inlinetext.png "0903-09_InlineText")  
  
 **Texte de Server Explorer en ligne : l’actualisation...**  
  
##### <a name="tool-windows"></a>Fenêtres d’outil  
 Indication de la progression globale est représentée par une barre de progression indéterminée placée directement sous la barre d’outils.  
  
 ![Barre de progression indéterminée globale](~/extensibility/ux-guidelines/media/0903-23_globalindeterminate.png "0903-23_GlobalIndeterminate")  
  
 **Barre de progression indéterminée globale de Team Explorer**  
  
##### <a name="dialogs"></a>Boîtes de dialogue  
 Boîtes de dialogue peuvent contenir les types de chargeur de progression. Indicateurs de progression peuvent être associées à la messagerie ainsi que combinées avec plusieurs niveaux d’indication de progression pour représenter granulaire et sous-processus.  
  
 ![Boîte de dialogue avec plusieurs types d’indicateurs de progression](~/extensibility/ux-guidelines/media/0903-11_dialog.png "0903-11_Dialog")  
  
 **Boîte de dialogue Visual Studio avec plusieurs types d’indicateurs de progression et les processus simultanés**  
  
 ![Boîte de dialogue avec messagerie et chargeur de progression](~/extensibility/ux-guidelines/media/0903-12_dialog2.png "0903-12_Dialog2")  
  
 **Boîte de dialogue Visual Studio avec les commandes en ligne de messagerie et chargeur de progression**  
  
##### <a name="document-well"></a>Document bien  
 Le document peut également afficher plusieurs types de chargeur de progression en association avec des contrôles.  
  
 ![Messagerie de progression dans le document de configuration](~/extensibility/ux-guidelines/media/0903-13_documentwell.png "0903-13_DocumentWell")  
  
 **Barre de progression indéterminée sous la barre d’outils**  
  
##### <a name="output-window"></a>Fenêtre Sortie  
 La fenêtre de sortie est appropriée pour la gestion des processus progression et l’état de progression en cours via la messagerie textuelle inline. Vous devez utiliser la barre d’état, ainsi que n’importe quel rapport de progression de fenêtre de sortie.  
  
 ![Messagerie de progression dans la fenêtre sortie](~/extensibility/ux-guidelines/media/0903-14_outputwindow.png "0903-14_OutputWindow")  
  
 **La fenêtre de sortie avec l’état du processus en cours et attente de messagerie**  
  
##  <a name="a-namebkmkinfobarsa-infobars"></a><a name="BKMK_Infobars"></a>Barres  
  
### <a name="overview"></a>Vue d'ensemble  
 Barres donner à l’utilisateur un indicateur proche de leur point d’attention et l’utilisation du contrôle de barre d’informations partagées garantit la cohérence dans apparence visuelle et d’interaction.  
  
 ![Barre d’informations](~/extensibility/ux-guidelines/media/0904-01_infobar.png "0904-01_Infobar")  
  
 **Barres dans Visual Studio**  
  
#### <a name="appropriate-uses-for-an-infobar"></a>Conditions d’utilisation d’une barre d’informations  
  
-   Pour permettre à l’utilisateur un message non bloquant mais important pertinente dans le contexte actuel  
  
-   Pour indiquer que l’interface utilisateur est dans un état ou une condition qui achemine des implications d’interaction, telles que le débogage d’historique  
  
-   Pour informer l’utilisateur que le système a détecté des problèmes tels que lorsqu’une extension est à l’origine des problèmes de performances  
  
-   Pour fournir à l’utilisateur un moyen de tirer facilement action, par exemple lorsque l’éditeur détecte qu’un fichier a mixte tabulations et espaces  
  
##### <a name="do"></a>Faire :  
  
-   Créez la barre d’informations du message courtes au point.  
  
-   Conserver le texte sur les liens et les boutons concise.  
  
-   Vérifiez les options « action » que vous fournissez aux utilisateurs sont minimes, affichant uniquement les actions requises.  
  
##### <a name="dont"></a>Ne pas :  
  
-   Utilisez une barre d’informations pour offrir des commandes standards qui doivent être placés dans une barre d’outils.  
  
-   Utilisez une barre d’informations à la place d’une boîte de dialogue modale.  
  
-   Créer un message en dehors d’une fenêtre flottant.  
  
-   Utilisez plusieurs barres dans plusieurs emplacements dans la même fenêtre.  
  
#### <a name="can-multiple-infobars-show-at-the-same-time"></a>Plusieurs barres peuvent afficher en même temps ?  
 Oui, plusieurs barres peut afficher en même temps. Ils seront affichera dans l’ordre premier arrivé, premier servi avec la première barre d’informations affichant sur Affichage barres supérieure et supplémentaires ci-dessous.  
  
 L’utilisateur verra un maximum de trois barres à la fois, après qui, si plusieurs barres sont disponibles, la région de la barre d’informations sera permettant le défilement.  
  
### <a name="creating-an-infobar"></a>Création d’une barre d’informations  
 La barre d’informations comprend quatre sections, de gauche à droite :  
  
-   **Icône :** c’est ici que vous ajoutez une icône vous souhaitez afficher la barre d’informations, par exemple une icône d’avertissement.  
  
-   **Texte :** vous pouvez ajouter le texte pour décrire l’utilisateur scénario/situation, ainsi que des liens dans le texte, si nécessaire. Veillez à conserver le texte concise.  
  
-   **Actions :** cette section doit contenir des liens et des boutons pour les actions que l’utilisateur peut choisir dans votre barre d’informations.  
  
-   **Bouton Fermer :** la dernière section vers la droite peut avoir un bouton Fermer.  
  
#### <a name="creating-a-standard-infobar-in-managed-code"></a>Création d’une barre d’information standard dans le code managé  
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
  
 ![Barre d’informations avec lien hypertexte](~/extensibility/ux-guidelines/media/0904-02_infobarhyperlink.png "0904-02_InfobarHyperlink")  
  
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
 L’implémentation de InfoBarModel ou IVsInfoBar sont des modèles de données doivent être convertis en un UIElement pour pouvoir être affichés dans l’interface utilisateur. Un UIElement peut être récupéré auprès du service SVsInfoBarUIFactory/IVsInfoBarUIFactory.  
  
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
 Barres peuvent être affichées dans une ou plusieurs des emplacements suivants :  
  
-   Fenêtres d’outil  
  
-   Dans un onglet de document  
  
> [!IMPORTANT]
>  Il est possible de placer une barre d’informations pour donner un message sur le contexte global. Il apparaît entre les barres d’outils et le document bien. Cette n’est pas recommandée, car il provoque des problèmes avec « raccourcis et jerk » de l’IDE et doit être évitée, sauf si cela est absolument nécessaire et approprié.  
  
#### <a name="placing-an-infobar-in-a-toolwindowpane"></a>Placer une barre d’informations dans un ToolWindowPane  
 La méthode ToolWindowPane.AddInfoBar(IVsInfoBar) peut être utilisée pour ajouter une barre d’informations à une fenêtre outil. Cette API peut ajouter un IVsInfoBar (le InfoBarModel est une implémentation par défaut), ou un IVsUIElement.  
  
#### <a name="placing-an-infobar-in-a-document-or-non-toolwindowpane"></a>Placer une barre d’informations dans un document ou un non ToolWindowPane  
 Pour placer une barre d’informations dans n’importe quel IVsWindowFrame, utilisez la propriété VSFPROPID_InfoBarHost pour obtenir le IVsInfoBarHost pour le frame, puis ajoutez la barre d’informations UIElement.  
  
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
 Pour placer une barre d’informations dans la fenêtre principale, le VSSPROPID_MainWindowInfoBarHost du service IVsShell permet d’obtenir IVsInfoBarHost la fenêtre principale et lui ajouter la barre d’informations UIElement à.  
  
### <a name="will-i-know-when-the-user-takes-action-in-my-infobar"></a>Savoir quand l’utilisateur exécute l’action dans ma barre d’informations ?  
 Oui, nous renvoie chaque action d’événement à l’auteur de la barre d’informations. Il revient ensuite l’auteur de la barre d’informations pour prendre des mesures dans l’IDE en fonction de la sélection de l’utilisateur dans la barre d’informations. Barres sera automatiquement supprimée à partir de l’hôte dont bouton Fermer, mais le travail supplémentaire est nécessaire si d’autres barres doivent être supprimés après la fermeture. Télémétrie devrez également être enregistrés séparément par chaque barre d’informations.  
  
#### <a name="receiving-infobar-events-in-a-toolwindowpane"></a>Recevoir des événements de la barre d’informations dans un ToolWindowPane  
 ToolWindowPane comporte deux événements de barres. L’événement InfoBarClosed est déclenché lorsqu’une barre d’informations dans le ToolWindowPane est fermée. L’événement InfoBarActionItemClicked est déclenché lorsque l’utilisateur clique sur un lien hypertexte ou un bouton dans la barre d’informations.  
  
#### <a name="receiving-infobar-events-directly-from-the-uielement"></a>Recevoir des événements de la barre d’informations directement à partir de UIElement  
 IVsInfoBarUIElement.Advise permet de s’abonner aux événements directement à partir UIElement d’une barre d’informations. L’implémentation IVsInfoBarUIEvents permettra à l’auteur de près de réception et les événements de clic.  
  
```  
public interface IVsInfoBarUIEvents  
{  
    void OnActionItemClicked(IVsInfoBarUIElement infoBarUIElement, IVsInfoBarActionItem actionItem);  
    void OnClosed(IVsInfoBarUIElement infoBarUIElement);  
}  
  
```  
  
##  <a name="a-namebkmkerrorvalidationa-error-validation"></a><a name="BKMK_ErrorValidation"></a>Validation de l’erreur  
 Lorsqu’un utilisateur entre des informations qui ne sont pas acceptables, par exemple lorsqu’un champ obligatoire est ignoré ou lorsque les données entrées dans un format incorrect, il est préférable d’utiliser contrôle validation ou des commentaires près du contrôle au lieu d’utiliser une boîte de dialogue d’erreur bloquante.  
  
### <a name="field-validation"></a>Validation de champ  
 Validation de formulaire et le champ se compose de trois composants : un contrôle, une icône et une info-bulle. Bien que plusieurs types de contrôles peuvent utiliser cette option, une zone de texte sera utilisée comme un exemple.  
  
 ![Champ de validation (vide)](~/extensibility/ux-guidelines/media/0905-01_fieldvalidation.png "0905-01_FieldValidation")  
  
 Si le champ est obligatoire, il convient de filigrane affiche un message indiquant ** \<requis >** et l’arrière-plan du champ doit être clair jaune (VSColor : `Environment.ControlEditRequiredBackground`) et gris au premier plan (VSColor : `Environment.ControlEditRequiredHintText`) :  
  
 ![Champ de validation avec étiquette « Obligatoire »](~/extensibility/ux-guidelines/media/0905-02_fieldvalidationrequired.png "0905-02_FieldValidationRequired")  
  
 Le programme peut déterminer que le contrôle est dans un état de *contenu non valide entré* lorsque le focus est déplacé vers un autre contrôle ou lorsque l’utilisateur clique sur un bouton de validation [OK] ou lorsque l’utilisateur enregistre le document ou le formulaire.  
  
 Lorsque l’état du contenu non valide est détecté, une icône apparaît dans le contrôle ou juste à côté de lui. Pointage de l’icône ou le contrôle, une info-bulle qui décrit l’erreur doit apparaître. En outre, une bordure de 1 pixel doit apparaître autour du contrôle qui crée l’état non valide.  
  
 ![Spécifications de disposition de validation de champ](~/extensibility/ux-guidelines/media/0905-03_layoutspecs.png "0905-03_LayoutSpecs")  
  
 **Spécifications de disposition pour la validation de champ**  
  
#### <a name="acceptable-variations-for-icon-location"></a>Variations acceptables pour l’emplacement de l’icône  
 Il existe des cas uniques innombrables dans lequel les utilisateurs doivent être informés sur les erreurs de validation. Si l'on considère le type de contrôle et la configuration de l’interface utilisateur, choisissez le positionnement de l’icône correspondant à votre situation.  
  
 ![Emplacements acceptables pour l’emplacement de l’icône](~/extensibility/ux-guidelines/media/0905-04_iconlocation.png "0905-04_IconLocation")  
  
 **Variations acceptables pour les emplacements d’icône de validation de champ**  
  
#### <a name="validation-requiring-a-round-trip-to-a-server-or-network-connection"></a>Validation nécessitant un aller-retour vers un serveur ou une connexion réseau  
 Dans certains cas, un aller-retour vers le serveur est nécessaire pour vérifier le contenu et il est important afficher la progression de l’utilisateur, vérifié et les États d’erreur. La figure ci-dessous montre un exemple de ce cas et l’interface utilisateur recommandée.  
  
 ![Validation impliquant un aller-retour vers un serveur](~/extensibility/ux-guidelines/media/0905-05_roundtrip.png "0905-05_RoundTrip")  
  
 **Validation impliquant un aller-retour vers un serveur**  
  
 Notez que l’espace disponible suffisant à droite du contrôle doit être fournie pour s’adapter à « Vérification... » et le texte « Réessayer ».  
  
#### <a name="in-place-warning-text"></a>Texte d’avertissement sur place  
 Lorsque l’espace disponible pour placer le message d’erreur proche du contrôle dans un état d’erreur est, il est préférable à l’aide de l’info-bulle uniquement.  
  
 ![Avertissement sur place](~/extensibility/ux-guidelines/media/0905-06_inplacewarning.png "0905-06_InPlaceWarning")  
  
 **Texte d’avertissement sur place**  
  
#### <a name="watermarks"></a>Filigranes  
 Parfois, une fenêtre ou un contrôle entier est dans un état d’erreur. Dans ce cas, utilisez un filigrane pour indiquer l’erreur.  
  
 ![Filigrane](~/extensibility/ux-guidelines/media/0905-07_watermark.png "0905-07_Watermark")  
  
 **Validation de champ filigrane**
