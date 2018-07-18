---
title: Texte d’interface utilisateur et l’aide de Visual Studio | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: e8747d07-6c90-46cc-b425-55b589f7e9e4
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 697c794d17f3004b0f37e668ff67afb703490e18
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31148364"
---
# <a name="ui-text-and-help-for-visual-studio"></a>Texte d’interface utilisateur et l’aide de Visual Studio
##  <a name="BKMK_UITextAndTerminology"></a> La terminologie et le texte d’interface utilisateur  
 Texte compréhensible est essentiel pour l’interface utilisateur effectif. Les utilisateurs de logiciels ont tendance à lire les étiquettes en premier lieu, à savoir celles les plus pertinents à la fin de la tâche en cours. Lecture du texte statique avec une fréquence inférieure. Plan pour les utilisateurs à démarrer une analyse rapide de la fenêtre entière, suivie d’une lecture de l’interface utilisateur dans cet ordre approximatif leurs sessions de travail :  
  
1.  Contrôles interactifs dans le centre  
  
2.  Valider des boutons  
  
3.  Contrôles interactifs trouvées ailleurs  
  
4.  Instructions principales  
  
5.  Obtenir des explications supplémentaires  
  
6.  Titre de la fenêtre  
  
7.  Tout autre texte statique dans le corps principal  
  
### <a name="usage-patterns-for-ui-text"></a>Modèles d’utilisation pour le texte de l’interface utilisateur  
  
#### <a name="title-bar-text"></a>Texte de barre de titre  
 Texte de barre de titre doit correspondre à la commande qui a engendré l’interface utilisateur.  
  
#### <a name="instructional-text-helper-text"></a>Texte d’instructions (texte d’aide)  
 Dans certaines boîtes de dialogue, il est utile fournir des instructions principales visibles pour expliquer comment procéder dans la fenêtre ou dans la page. Cela est parfois appelée « texte d’aide. »  
  
##### <a name="writing-style-rules-for-helper-text"></a>L’écriture des règles de style pour le texte d’aide  
  
-   N’expliquent pas les évidents. Sauf si elle est absolument nécessaire, n’incluez pas le texte d’instructions.  
  
-   Texte d’instructions est toujours placé en haut de la boîte de dialogue et doit faire référence à la tâche en cours d’exécution.  
  
-   Précisément expliquer aux utilisateurs qu’ils doivent faire. Éviter la redondance et la communication excessive.  
  
-   Passez en revue chaque fenêtre et éliminer les instructions et les mots en double.  
  
-   Conserver le texte d’instructions court. Si plus d’informations est nécessaire pour certains utilisateurs ou scénarios, puis fournissez un lien vers une rubrique en ligne conceptuel détaillée.  
  
-   Écrivez votre texte afin que chaque mot conserve le poids et n’est nécessaire.  
  
-   Suivez les recommandations de Microsoft existante pour [texte de l’Interface utilisateur](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742478\(v=vs.85\).aspx) et [Style et ton](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742477\(v=vs.85\).aspx).  
  
#### <a name="supplemental-instructions"></a>Obtenir des instructions supplémentaires  
 Obtenir des instructions supplémentaires fournissent des informations supplémentaires qui aide l’utilisateur à comprendre les contrôles ou regroupements de contrôle. Cela peut également inclure le texte d’indication nécessaire de comprendre le format utilisé par le contrôle d’entrée est attendu. Utilisez les instructions supplémentaires avec parcimonie. Réserver aux cas où il est probable que l’utilisateur ne sont pas comprendre pleinement les conséquences du choix qu’ils font.  
  
 ![Texte supplémentaire dans Visual Studio](../../extensibility/ux-guidelines/media/0601-b_supplementaltext1.png "0601-b_SupplementalText1")  
  
 **Texte supplémentaire dans Visual Studio**  
  
 ![Texte supplémentaire dans Visual Studio](../../extensibility/ux-guidelines/media/0601-c_supplementaltext2.png "0601-c_SupplementalText2")  
  
 **Texte supplémentaire dans Visual Studio**  
  
#### <a name="infotips"></a>Info-bulles  
 Souvent, le texte d’instructions est peut-être trop long pour positionner sur place dans l’interface utilisateur ou peut être utile uniquement aux nouveaux utilisateurs, sensation encombrement aux utilisateurs expérimentés. Dans ce cas, le texte d’instructions / d’information doit être placé dans une info-bulle dans une info-bulle.  
  
 Info-bulles doivent être placés près les contrôles qu’ils sont liés à et doivent utiliser l’icône d’info-bulle spécifique, qui n’est pas discrète notable.  
  
 ![Info-bulle dans Visual Studio](../../extensibility/ux-guidelines/media/0601-d_infotip.png "0601-d_InfoTip")  
  
 **Exemple d’une info-bulle dans Visual Studio**  
  
##### <a name="writing-style-rules-for-infotips"></a>Règles de style d’écriture pour les info-bulles  
  
-   Écrire des info-bulles comme phrases complètes. Ils nécessitent des verbes spécifiques, le cas de phrase et la ponctuation de fin.  
  
-   Utiliser des info-bulles pour compléter l’instruction principale ou vos informations. Si vous utilisez simplement les différents mots de retraiter l’idée principale, vous n’avez pas besoin une info-bulle.  
  
-   Conserver les info-bulles bref. Utiliser des mots petits et brut, langage courant qui prend en charge et encourage l’utilisateur.  
  
-   Suivez les recommandations de Microsoft existante pour [texte de l’Interface utilisateur](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742478\(v=vs.85\).aspx) et [Style et ton](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742477\(v=vs.85\).aspx).  
  
#### <a name="control-labels"></a>Étiquettes de contrôle  
 Étiquettes de contrôle doivent être court et concis et suivez le [des conseils de bureau Windows pour les contrôles](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742399\(v=vs.85\).aspx).  
  
 Pour plus d’informations sur le format d’étiquette de contrôle et l’emplacement dans l’interface utilisateur, consultez [disposition pour Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md).  
  
#### <a name="help-links"></a>Liens d’aide  
 Liens d’aide peuvent soit être placés dans le texte d’instructions ou dans le corps de l’interface utilisateur. Ils peuvent être des liens vers l’aide ou lancez l’internes boîtes de dialogue.  
  
##### <a name="visual-style-rules-for-help-links"></a>Règles de style visuel pour les liens d’aide  
  
-   Utiliser les couleurs de l’environnement approprié pour les liens hypertexte. Un lien hypertexte appliqué correctement pas brièvement clignote en rouge quand vous cliquez dessus. S’il s’affiche, puis il indique que les couleurs de l’environnement ne sont pas utilisés.  
  
-   Soulignements doivent uniquement être utilisées sur pointage ou lorsque le lien est incorporé dans un paragraphe.  
  
-   Pour plus d’informations sur les styles visuels et d’interaction pour les liens hypertexte, voir les boutons et les liens hypertexte.  
  
##### <a name="writing-style-rules-for-help-links"></a>L’écriture des règles de style pour les liens d’aide  
  
-   Lors du lancement de boîtes de dialogue, mettre à jour les normes pour les points de suspension : aucune sélection pour la navigation, si la tâche requiert une interface utilisateur supplémentaire des points de suspension.  
  
     ![Lien d’aide dans Visual Studio](../../extensibility/ux-guidelines/media/0601-e_helplink.png "0601-e_HelpLink")  
  
     **Points de suspension (...) dans un lien d’aide indique que la tâche nécessite une interface utilisateur supplémentaire.**  
  
-   Liens ne doivent pas commencer avec « Apprentissage », car il se n'agit pas intention de l’utilisateur. L’utilisateur souhaite répondre à une question spécifique, pas recevoir une formation générale.  
  
-   Les liens d’aide d’une expression afin qu’ils poser la question que va répondre à la rubrique.  
  
     Incorrect :  
     « En savoir plus sur la tarification Windows Azure Mobile Services »  
  
     Corriger :  
     « Les options de tarification sont disponibles pour Windows Azure Mobile Services ? »  
  
-   N’utilisez jamais *cliquez sur...*  pour le texte du lien.  
  
-   Ne liez jamais uniquement le mot « ici ». Cela peut être problématique pour certains lecteurs d’écran, qui seront vocaux uniquement le mot contenant des liens hypertexte.  
  
     Incorrect :  
     « Trouver plus d’informations sur Windows Azure Mobile Services **ici**»  
  
     Corriger :  
     « Les options de tarification sont disponibles pour Windows Azure Mobile Services ? »  
  
-   Pour plus d’informations sur le style d’écriture correcte pour les liens d’aide, consultez le [des conseils de bureau Windows de l’aide](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742494\(v=vs.85\).aspx).  
  
#### <a name="hint-text"></a>Texte d’indication  
 Texte d’information apparaît en filigrane dans un contrôle ou sous le contrôle. Mise en forme correcte est appliqué à l’aide du jeton VSColors approprié, `Environment.GrayText`.  
  
 Il peut apparaître dans plusieurs formes.  
  
-   À la place de l’étiquette de contrôle :  
  
     ![Indicateur de texte dans Visual Studio](../../extensibility/ux-guidelines/media/0601-f_hinttext1.png "0601-f_HintText1")  
  
-   Avec un verbe, ce qui donne des instructions :  
  
     ![Indicateur de texte dans Visual Studio](../../extensibility/ux-guidelines/media/0601-g_hinttext2.png "0601-g_HintText2")  
  
-   Avec le texte qui indique une entrée requise :  
  
     ![Indicateur de texte dans Visual Studio](../../extensibility/ux-guidelines/media/0601-h_hinttext3.png "0601-h_HintText3")  
  
#### <a name="watermark-text"></a>Texte de filigrane  
 Sur une aire de conception vide, le texte doit indiquer ce qu’il faut faire ainsi que pour fournir des liens pour ouvrir d’autres fenêtres connexes, le cas échéant :  
  
 ![Filigrane du texte dans Visual Studio](../../extensibility/ux-guidelines/media/0601-i_watermarktext.png "0601-i_WatermarkText")  
  
 **Exemple de texte de filigrane dans Visual Studio**  
  
### <a name="common-terminology"></a>Terminologie commune  
  
|Terme|Explication|Commentaire|  
|----------|-----------------|-------------|  
|Se connecter / déconnecter|Verbes utilisés indifféremment avec le site web pour représenter l’authentification dans une propriété web. Dans les clients, nous utilisons cette fois en tant qu’une notion de niveau supérieur pour la signature et la connexion utilisateur IDE, ce qui représente une identité de niveau supérieur qui fournit des fonctionnalités de niveau supérieur telles que l’itinérance et les licences qui ne sont pas disponibles avec toutes les autres connexions.|L’utilisateur de l’IDE est la seule fonctionnalité qui doit représenter une connexion / déconnexion verbe, car il représente l’utilisateur IDE de niveau supérieur.|  
|Connecter / déconnecter|Utilisez les emplacements où une fonctionnalité conserve une seule connexion à un service en ligne.|L’Explorateur de serveurs, où vous ne pouvez avoir qu’une seule connexion d’Azure active à la fois, est un exemple de connecter/déconnecter.|  
|Ajouter / supprimer|Non destructrice. À utiliser lorsque l’ajout ou la suppression d’un élément dans une liste.|La boîte de dialogue liste de serveur TFS Connection Manager est un exemple d’ajout/suppression.|  
|Supprimer|Destructeur. Utilisez uniquement lorsque l’élément en cours de suppression est définitivement ignorée ou supprimé à partir du disque.|« Delete » requiert généralement une invite si le résultat de la suppression d’un fichier à partir du disque.|  
  
## <a name="error-messages"></a>Messages d’erreur  
  
### <a name="overview"></a>Vue d'ensemble  
 Erreurs se produisent. Définition des limitations sur l’utilisateur peut effectuer est une première étape pratique pour empêcher des messages d’erreur évitables. Toutefois, lorsqu’une erreur se produit, un message d’erreur bien écrite peut atteindre permettent d’atténuer le problème. Messages d’erreur sont sans doute un des plus importants types de notification que l’utilisateur voit, car ils sont synchrones et indiquent un problème qui doit être résolu. Messages d’erreur mal écrite laissent les utilisateurs sur leurs propres pour déterminer la cause des erreurs et les solutions possibles.  
  
 Les utilisateurs peuvent arrêter attention à l’utilisation excessive ou confusion entre les messages d’erreur, afin de l’expérience de l’écriture des messages uniquement nécessaires qui renforcent la valeur de l’utilisateur. Si le message est simplement une notification, utilisez une autre présentation.  
  
### <a name="rules-for-creating-an-error-message"></a>Règles de création d’un message d’erreur  
  
-   Lors de la construction de messages d’erreur, choisissez le niveau d’erreur approprié pour le public. Objectif pour les résumés simples qui fournissent une action de l’utilisateur peut prendre, le cas échéant. État de ne pas tout ce que l’utilisateur n’a pas besoin de connaître.  
  
-   Fournir une assistance implicite. Il est plus facile à lire et d’agir sur un message d’erreur qui contient l’instruction.  
  
-   N’utilisez pas deux négatifs.  
  
-   Effectuer les deux un moyen automatisé et vérifier tout message d’erreur que vous écrivez une grammaire manuelle et l’orthographe.  
  
-   Pour les messages d’erreur complexes, évitez des communications séquentielles. N’utilisez jamais un raccordement F1 pour le message d’erreur. Le message lui-même doit être suffisant.  
  
-   Utilisez l’icône appropriée.  
  
-   Vérifiez les questions faciles à comprendre et utiliser les boutons qui ont le choix clair, tels que « Delete » et « Annuler ».  
  
-   Pour les avertissements, être clairement ce que sera la conséquence de continuer. Les boutons doivent indiquer la conséquence.  
  
-   Pour les erreurs, décrivent ce que l’utilisateur peut faire pour résoudre le problème. Boutons doivent être des actions ou dites « Clôture ». N’utilisez pas un bouton « OK » pour un message d’erreur.  
  
-   Questions à poser lors de la construction d’un message d’erreur :  
  
    -   L’utilisateur peut comprendre comment résoudre le problème avec cette erreur uniquement ?  
  
    -   L’utilisateur utilise-t-il le vocabulaire de même que cette erreur ?  
  
    -   Est cette ambigious erreur ou partagés dans plusieurs situations ? Dans ce cas, comment vous guider les utilisateurs à la solution que dont ils ont besoin ?  
  
#### <a name="build-errors"></a>Erreurs de build  
 Étant donné que Visual Studio est un outil de développement de logiciels, de nombreux de ses composants ont une compilation, la conversion ou de codage d’étape pour le travail du développeur de convertir au format binaire. Ces conversions peuvent provoquer des erreurs lorsque le compilateur ne peut pas traiter les fichiers créés de manière incorrecte ou lorsque les options du compilateur n’ont pas été définies correctement.  
  
 Les utilisateurs de Visual Studio peuvent passer un nombre important d’heures de développement résolution des erreurs de build. Ce temps de résolution augmente lorsque les erreurs ont des dépendances ou lorsque les messages d’erreur sont mal écrit, ce qui peut rendre difficile à découvrir la source de l’erreur.  
  
 Des erreurs de build sont ceux qui ne se produisent pas dans le premier emplacement, c’est pourquoi Visual Studio fournit la saisie semi-automatique et les tildes IntelliSense. Programmes de validation de schéma et les outils fournissent le même type de retour. Ces mécanismes guident proactive de l’utilisateur pour construire du code correct, en réduisant le risque d’erreurs de build.  
  
 Visual Studio fournit une fenêtre outil dans lequel les utilisateurs peuvent lire et parcourir les erreurs qui se sont produites dans leurs fenêtres de document. Raccourcis clavier sont fournies afin que l’utilisateur peut naviguer rapidement grandes quantités de code et aller directement à l’emplacement du problème. Visual Studio permet également de chaque erreur de build être lié à un ID de mot clé/contexte d’aide particulier afin que l’utilisateur peut accéder directement à une rubrique d’aide qui fournit des informations plus détaillées sur l’erreur.  
  
 Erreurs de build claire et concise, d’écriture :  
  
-   **Utilisez un langage simple** expliquant le problème avec peu ou pas jargon de compilateur. Le texte d’une erreur de build ne doit pas être trop technique.  
  
-   **Montrer les causes possibles.** Par exemple, « manquant un signe deux-points entre la propriété et la valeur dans le ' (propriété) : (valeur)' déclaration. »  
  
-   Fournissez des détails sur les corrections éventuelles. Si l’espace n’est pas suffisant, des détails supplémentaires peuvent être mis dans la rubrique d’aide correspondante.  
  
### <a name="components-of-a-well-written-error-message"></a>Composants d’un message d’erreur bien écrite  
  
#### <a name="use-the-shell-dialog-service-for-error-messages"></a>Utiliser le service de boîte de dialogue d’interpréteur de commandes pour les messages d’erreur.  
 Le service de boîte de dialogue d’interpréteur de commandes vous permet de contrôler l’apparence du message, polices, en particulier, sans les principales modifications apportées aux éléments individuels. Utilisez le **IErrorInfo** mécanismes et les signaler à l’aide de **IVsUIShell::SetErrorInfo/ReportErrorInfo**.  
  
#### <a name="choose-an-effective-and-appropriate-notification-presentation"></a>Choisissez une présentation de la notification efficace et appropriée.  
 Utilisez une boîte de dialogue modale avec un avertissement critique si une action immédiate est nécessaire pour éviter la perte de données (notification synchrone). Icônes critiques sont réservés pour les situations dans le message sans effectuer de lecture de fermeture, il peut entraîner de conséquences négatives. Perte de données est une situation critique qui requiert une réponse au niveau de l’alerte. Utilisation excessive de l’icône critique desensitizes aux utilisateurs de son importance. Si le message d’erreur est de nature informative, envisagez d’alternatives à une boîte de dialogue modale (notification asynchrone).  
  
#### <a name="provide-a-clean-succinct-explanation-of-why-the-problem-occurred-rather-than-a-technical-explanation"></a>Fournir une explication propre et concise de la cause du problème au lieu d’une explication technique.  
 Surcharger les utilisateurs avec les détails techniques dans l’explication rend les plus susceptibles d’ignorer les messages d’erreur. Exemples de bon de messagerie :  
  
-   « Impossible d’ouvrir le fichier demandé. »  
  
-   « Impossible de se connecter à Internet. »  
  
#### <a name="provide-information-about-how-to-fix-the-problem"></a>Fournissent des informations sur la façon de résoudre le problème.  
 Des suggestions l’utilisateur pour résoudre le problème. Être objective avec l’utilisateur s’il n’y a aucune suggestion. Fournit des liens directs vers d’autres sources en ligne, telles que le support technique ou le support de la Communauté. Essayez de renvoyer les utilisateurs à des informations en ligne spécifiques se rapportant à ce problème. Pour un ID d’erreur, envisagez d’associer les utilisateurs à un thread de discussion sur cette erreur spécifique. Exemples de bon de messagerie :  
  
-   « Vérifiez que vous êtes connecté à Internet et recommencez cette opération. »  
  
-   « Assurez-vous que le fichier existe et que vous êtes autorisé à ouvrir. »  
  
#### <a name="write-a-message-that-is-short-and-to-the-point"></a>Écrit un message est court et au point.  
 Un message d’erreur peut notifier, expliquer et offrent une solution, mais toujours ignoré s’il est trop long. Une solution consiste à utiliser une divulgation progressive avec un bouton de détails. Par exemple, donner une courte description/solution, puis entrer plus de détails sous un bouton Détails. Si les utilisateurs choisissent pour en savoir plus sur l’erreur, il peuvent le faire.  
  
 La langue dans le message doit être :  
  
-   **Domaine approprié.** Utilisez le langage que comprendre l’utilisateur. Bien que nos clients sont des développeurs, ils souvent n’ont pas le contexte et la terminologie que nous avons.  
  
-   **Spécifique.** Évitez les vagues libellé et donner des noms spécifiques et les emplacements des objets impliqués. Par exemple, un message d’erreur comme « caractère n’est pas valide » n’est pas utile. Le caractère ? « Fichier introuvable ». Le fichier ?  
  
-   **Courtois.** Ne l’utilisateur blâmez Rabaissez. Éviter de langage hostile ou choquant (kill, exécuter, arrêter, irrécupérable, non conforme). Évitez le texte en majuscules, qui est souvent perçu comme trouver et n’est pas comme accessible en lecture. N’utilisez pas humeur.  
  
-   **Corriger.** Utilisez corriger l’orthographe et grammaire (même en alpha). Un et gênant sont des fautes de frappe.  
  
-   **En fonction du contexte approprié.** Utilisez le texte du bouton approprié. Éviter le bouton « OK » et l’utiliser à la place de « Continue » ou « Oui/non ».  
  
### <a name="error-message-examples"></a>Exemples de message d’erreur  
  
|Bon|Incorrecte|  
|----------|---------|  
|« Le nombre que vous avez composé n’est plus en service. Veuillez vérifier le numéro et recomposer ou composez le 0 pour l’opérateur. »|-« Erreur (449) : nombre non conforme »<br />-« Cette erreur d’exception non gérée indique que l’opération a réussi. »<br /><br /> ![Message d’erreur incorrect dans Visual Studio](../../extensibility/ux-guidelines/media/0602-a_errordialog.png "0602-a_ErrorDialog")|  
  
## <a name="accessing-help"></a>Accéder à l’aide  
  
### <a name="overview"></a>Vue d'ensemble  
 En plus de documentation dans MSDN, un utilisateur de Visual Studio possède plusieurs points d’accès pour aider l’utilisateur dans l’interface utilisateur. Pour vous assurer que ces points d’accès sont constamment disponibles, les équipes de fonctionnalité doivent tirer parti du système d’aide proposé par l’environnement. Ces points d’accès sont :  
  
-   **Texte supplémentaire et les instruction dans les boîtes de dialogue.** Texte statique qui donne des explications, soit sur l’interface utilisateur de surface ou disponible sur une icône d’info-bulle au passage du curseur ou la direction.  
  
-   **Aide (F1)** (éditeur uniquement). Dans l’éditeur Visual Studio, un utilisateur peut faire confiance qu’à tout moment, en appuyant sur F1 s’affiche une rubrique d’aide spécifique à la sélection actuelle. Assurez-vous que les rubriques associées F1 sont appropriés et informatifs.  
  
-   **Liens hypertexte vers des rubriques d’aide.** Un lien hypertexte dans une boîte de dialogue, une fenêtre outil ou une aire de conception qui ouvre une rubrique pour aider l’utilisateur en savoir plus sur une technologie, fonctionnalité ou plus d’informations sur la façon d’accomplir une tâche.  
  
-   **Mécanismes de l’interface utilisateur d’assistance, telles que les balises actives et les boîtes de dialogue de génération.** Ces mécanismes aider l’utilisateur à comprendre un élément d’interface utilisateur, ou facilitent une tâche, telles que des balises actives ou des boîtes de dialogue Générateur.  
  
-   **Boutons d’aide de l’interface utilisateur** (déconseillé). Un indicateur visible dans la barre de titre qui donne accès à la rubrique d’aide F1.  
  
### <a name="text"></a>Texte  
  
#### <a name="instructional-and-supplemental-text-in-dialogs"></a>Texte supplémentaire et les instruction dans les boîtes de dialogue  
 Dans les boîtes de dialogue qui prennent en charge des tâches complexes, il peut être nécessaire pour permettre à texte d’instructions dans l’interface utilisateur, souvent en haut de la boîte de dialogue ou à proximité des contrôles complexes. Consultez [UI texte et la terminologie](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology) pour plus d’informations sur la règle de style.  
  
#### <a name="infotips"></a>Info-bulles  
 Souvent, un texte d’instructions est peut-être trop long pour positionner sur place dans l’interface utilisateur ou peut être utile uniquement aux nouveaux utilisateurs, sensation encombrement aux utilisateurs expérimentés. Dans ce cas, le texte d’instructions / d’information doit être placé dans une info-bulle dans une info-bulle.  
  
 Info-bulles doivent être placés près les contrôles qu’ils sont liés à et doivent utiliser l’icône d’info-bulle spécifique, qui n’est pas discrète notable.  
  
 ![Info-bulle dans Visual Studio](../../extensibility/ux-guidelines/media/0601-d_infotip.png "0601-d_InfoTip")  
  
 **Exemple d’une info-bulle dans Visual Studio**  
  
### <a name="interactive-help-mechanisms"></a>Mécanismes d’aide interactives  
  
#### <a name="f1-help"></a>F1 Aide  
 Aide (F1) est requis dans un éditeur ou d’une aire de conception, mais pas ailleurs dans l’environnement Visual Studio.  
  
#### <a name="hyperlinks-to-help-topics"></a>Liens hypertexte vers des rubriques d’aide  
 Liens hypertexte peuvent être utilisés pour effectuer une action, naviguer dans l’IDE ou lancer l’aide dans un navigateur. Consultez [UI texte et la terminologie](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology) pour plus d’informations sur la langue et 07.10.01 boutons et des liens hypertexte pour connaître les instructions visual et la disposition.  
  
#### <a name="help--buttons-in-dialog-title-bars-deprecated"></a>Aide des boutons [ ?] dans la boîte de dialogue les barres de titre (déconseillées)  
 La plupart des cas, les boutons d’aide [ ?] dans la barre de titre des boîtes de dialogue sont déconseillés. Les rubriques de l’interface utilisateur ne font plus partie de notre modèle de document, et par conséquent il ne peut pas être une rubrique appropriée à lier à. Essentiellement, le bouton de barre de titre est la même chose que la touche F1, et qui n’est plus nécessaire dans les boîtes de dialogue. Dans certains cas, cela peut toujours servir en tant qu’indicateur que plus d’informations conceptuelles ou de procédure est disponible, bien que les liens hypertexte sont plus couramment utilisés dans l’interface utilisateur plus récente.  
  
##### <a name="dialogs-created-through-the-environment"></a>Boîtes de dialogue créées par l’environnement.  
 Nombreuses boîtes de dialogue shell sont créés via la **VBDialogBoxParam** (fonction). Cette fonction partagée a été mis à jour pour vous aider à déplacer les **aide** bouton à partir de la boîte de dialogue le **?** bouton tout en conservant une architecture qui offre une compatibilité descendante compatible et extensible.  
  
 Plus précisément, le **VBDialogBoxParam** fonction examine le modèle de boîte de dialogue pour un bouton dont l’ID est **IDHELP** (9) ou de l’étiquette est **aide** ou **& aide**. Si un bouton d’aide est trouvé, il est masqué et le **WS_EX_CONTEXTHELP** style est ajouté à la boîte de dialogue, ce qui place la **?** bouton de barre de titre de la boîte de dialogue.  
  
 Lorsque la boîte de dialogue est créé, il exécute un push de la procédure de boîte de dialogue sur une pile et appelle la boîte de dialogue avec une procédure de boîte de dialogue pré-traitement nommée **DialogPreProc**. Lorsque le **?** bouton est activé, il envoie un **WM_SYSCOMMAND** de **SC_CONTEXTHELP** à la boîte de dialogue. Le **DialogPreProc** capture cette commande et les modifications apportées à un **WM_HELP** message, ce qui est passé à la procédure de boîte de dialogue d’origine.  
  
 La plupart des boîtes de dialogue créés par l’environnement ont un bouton d’aide sur la boîte de dialogue. Lorsque la boîte de dialogue s’affiche, le bouton aide est automatiquement masquée et seule la **?** fonctionnement du bouton. Si le **?** bouton jamais supprimé ou modifié dans Windows, cette solution vous permet de rapidement remettre en place pour les boutons d’aide d’origine.  
  
 Cette solution hypothèses quatre qui peuvent provoquer des bogues :  
  
-   Bouton d’aide de la boîte de dialogue est **IDHELP** (9).  
  
-   La boîte de dialogue semble correcte lorsque le bouton aide est masqué.  
  
-   La boîte de dialogue ne remplace pas sa winproc.  
  
-   La boîte de dialogue n’est pas incorporé à l’intérieur d’une autre boîte de dialogue.  
  
 Si votre boîte de dialogue se trouve dans msenv et n’utilise pas **VBDialogBoxParam**, parti **VBDialogBoxParam** avant d’implémenter votre propre gestionnaire.  
  
##### <a name="dialogs-created-through-other-packages"></a>Boîtes de dialogue créées par d’autres packages  
 Vous pouvez implémenter votre propre solution pour les boîtes de dialogue qui résident en dehors de msenv. Pour une classe de boîte de dialogue partagé dans votre VSPackage, envisagez de déplacer le bouton à la barre de titre ou l’implémentation d’un gestionnaire sur chaque boîte de dialogue. Le code suivant est un squelette d’une implémentation pour vous aider à démarrer :  
  
```  
struct DLGPROCITEM  
{  
    FARPROC proc; // The info used to create the dialog.  
    DLGPROCITEM* procPrev;  
};  
  
DLGPROCITEM* g_dlgProcStack = NULL;  
  
// A dialog starter/wrapper function is used to push the new  
// dialog proc to the top of our dialog proc stack.  
  
int SomeDialogStarterFunction(hinst, id, proc, etc)  
{  
    if (g_dlgProcStack == NULL)  
    {  
        g_dlgProcStack = new DLGPROCITEM;  
        g_dlgProcStack->procPrev = NULL;  
    }  
    else  
    {  
        DLGPROCITEM* procItem = new DLGPROCITEM;  
        g_dlgProcStack->procPrev = g_dlgProcStack;  
        g_dlgProcStack = procItem;  
    }  
}  
  
// Pop this dialog proc off the dialog proc stack.  
  
DialogBoxIndirectParam...(...)  
{  
    DLGPROCITEM* procItem = g_dlgProcStack->procPrev;  
    delete g_dlgProcStack;  
    g_dlgProcStack = procItem;  
}  
  
// A wrapper dialog procedure will allow us to capture the  
// SC_CONTEXTHELP button on the title bar from Windows and  
// forward it as a simple WM_HELP message back to the dialog.  
  
INT_PTR CALLBACK DialogPreProc(HWND hwndDlg, UINT uMsg,  
    WPARAM wParam, LPARAM lParam)  
{  
    if (uMsg == WM_SYSCOMMAND && wParam == SC_CONTEXTHELP)  
    {  
        uMsg = WM_HELP;  
        wParam = 0;  
        lParam = 0;  
    }  
    return CallWindowProc((WNDPROC)g_dlgProcStack->proc,  
        hwndDlg, uMsg, wParam, lParam);  
}  
```  
  
##### <a name="help-buttons-in-managed-code"></a>Boutons d’aide dans le code managé  
 Il est facile dans le code managé de substituer le comportement par défaut de la fenêtre titre barre aide du bouton. Voici une application de démonstration complète qui illustre ce comportement. Fondamentalement, vous devez substituer de votre formulaire **WndProc** (méthode) et les incendies puis hors tension de l’aide (F1) des demandes quand un **SC_CONTEXTHELP** message est intercepté.  
  
```  
using System;  
using System.Windows.Forms;  
  
public class HelpForm : Form  
{  
    private const int SC_CONTEXTHELP = 0xF180;  
    private const int WM_SYSCOMMAND = 0x0112;  
  
    public HelpForm()  
    {  
        this.ClientSize = new System.Drawing.Size(300, 250);  
        this.HelpButton = true;  
        this.MaximizeBox = false;  
        this.MinimizeBox = false;  
        this.Name = "HelpForm";  
        this.Text = "Help Form";  
    }  
  
    protected override void WndProc(ref Message m)  
    {  
        if (m.Msg == WM_SYSCOMMAND && SC_CONTEXTHELP == (int)m.WParam)  
            ShowHelp();  
        else  
            base.WndProc(ref m);  
    }  
  
    private void ShowHelp()  
    {  
        MessageBox.Show("F1 Help goes here.");  
    }  
  
     [STAThread]  
    static void Main()  
    {  
        Application.EnableVisualStyles();  
        Application.EnableRTLMirroring();  
        Application.Run(new HelpForm());  
    }  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Mise en forme pour Visual Studio](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md)   
 [Mise en page pour Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md)   
 [Notifications et progression pour Visual Studio](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md)