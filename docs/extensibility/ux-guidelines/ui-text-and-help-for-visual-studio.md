---
title: UI Texte et aide pour Visual Studio (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e8747d07-6c90-46cc-b425-55b589f7e9e4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b3247aeaa702b59722471c7d28e98957f04f3e07
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698298"
---
# <a name="ui-text-and-help-for-visual-studio"></a>Texte de l’interface utilisateur et Aide pour Visual Studio
## <a name="ui-text-and-terminology"></a><a name="BKMK_UITextAndTerminology"></a>Texte et terminologie de l’interface utilisateur
 Le texte compréhensible est crucial pour une interface utilisateur efficace. Les utilisateurs de logiciels ont tendance à lire les étiquettes en premier, à savoir celles les plus pertinentes pour accomplir la tâche à accomplir. Le texte statique est lu avec moins de fréquence. Prévoyez aux utilisateurs de commencer leurs sessions de travail par un balayage rapide de l’ensemble de la fenêtre, suivi d’une lecture de l’interface utilisateur dans cet ordre approximatif :

1. Contrôles interactifs au centre

2. Boutons de validation

3. Contrôles interactifs trouvés ailleurs

4. Instructions principales

5. Explications supplémentaires

6. Titre de fenêtre

7. Autre texte statique dans le corps principal

### <a name="usage-patterns-for-ui-text"></a>Modèles d’utilisation pour le texte de l’interface utilisateur

#### <a name="title-bar-text"></a>Barre de titre Texte
 Le texte de barre de titre doit correspondre à la commande qui a engendré l’interface utilisateur.

#### <a name="instructional-text-helper-text"></a>Texte pédagogique (texte d’aide)
 Dans certains dialogues, il est utile de fournir des instructions principales proéminentes pour expliquer ce qu’il faut faire dans la fenêtre ou dans la page. C’est ce qu’on appelle parfois le « texte d’aide ».

##### <a name="writing-style-rules-for-helper-text"></a>Règles de style d’écriture pour le texte d’aide

- N’expliquez pas l’évidence. À moins qu’il ne soit absolument nécessaire, n’incluez pas de texte pédagogique.

- Le texte pédagogique est toujours placé en haut du dialogue et doit se référer à la tâche accomplie.

- Expliquez précisément aux utilisateurs ce qu’ils doivent faire. Évitez la communication excessive et la redondance.

- Examinez chaque fenêtre et éliminez les mots et les déclarations en double.

- Gardez le texte d’instruction court. Si plus d’informations sont nécessaires pour certains utilisateurs ou scénarios, puis fournir un lien vers un sujet conceptuel détaillé en ligne.

- Écrivez votre texte de sorte que chaque mot a du poids et est nécessaire.

- Suivez les conseils Microsoft existants pour [le texte d’interface utilisateur](/windows/desktop/uxguide/text-ui) et le style et la [tonalité](/windows/desktop/uxguide/text-style-tone).

#### <a name="supplemental-instructions"></a>Instructions supplémentaires
 Les instructions supplémentaires fournissent des informations supplémentaires qui aident l’utilisateur à comprendre les contrôles ou les groupes de contrôle. Cela pourrait également inclure le texte d’indice nécessaire pour comprendre quel format le contrôle des entrées attend. Utilisez des instructions supplémentaires avec parcimonie. Réservez-les pour les cas où il est probable que l’utilisateur ne comprendra pas pleinement les ramifications du choix qu’il fait.

 ![Texte supplémentaire dans Visual Studio](../../extensibility/ux-guidelines/media/0601-b_supplementaltext1.png "0601-b_SupplementalText1")

 **Texte supplémentaire dans Visual Studio**

 ![Texte supplémentaire dans Visual Studio](../../extensibility/ux-guidelines/media/0601-c_supplementaltext2.png "0601-c_SupplementalText2")

 **Texte supplémentaire dans Visual Studio**

#### <a name="infotips"></a>InfoTips InfoTips
 Souvent, le texte pédagogique peut être trop long pour positionner en place dans l’interface utilisateur ou peut être utile uniquement aux nouveaux utilisateurs, se sentant comme de l’encombrement pour les utilisateurs expérimentés. Dans ce cas, le texte pédagogique/informationnel doit être placé sous une pointe d’outils sous un InfoTip.

 InfoTips doit être placé près des contrôles auxquels ils sont liés et doivent utiliser l’icône spécifique InfoTip, qui est discrète mais perceptible.

 ![Info-bulle dans Visual Studio](../../extensibility/ux-guidelines/media/0601-d_infotip.png "0601-d_InfoTip")

 **Exemple d’InfoTip dans Visual Studio**

##### <a name="writing-style-rules-for-infotips"></a>Règles de style d’écriture pour InfoTips

- Écrivez InfoTips comme phrases complètes. Ils exigent des verbes spécifiques, un cas de phrase et une ponctuation de fin.

- Utilisez InfoTips pour compléter votre instruction principale ou des informations. Si vous utilisez simplement des mots différents pour réitérer l’idée principale, vous n’avez pas besoin d’un InfoTip.

- Gardez InfoTips court et doux. Utilisez de petits mots et un langage simple et quotidien qui soutient et encourage l’utilisateur.

- Suivez les conseils Microsoft existants pour [le texte d’interface utilisateur](/windows/desktop/uxguide/text-ui) et le style et la [tonalité](/windows/desktop/uxguide/text-style-tone).

#### <a name="control-labels"></a>Étiquettes de contrôle
 Les étiquettes de contrôle doivent être courtes, concises et suivre les [directives de Windows Desktop pour les contrôles](/windows/desktop/uxguide/controls).

 Pour plus d’informations sur le format de l’étiquette de contrôle et le placement dans l’interface utilisateur, consultez [Layout for Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md).

#### <a name="help-links"></a>Liens d’aide
 Les liens d’aide peuvent être placés dans le texte pédagogique ou dans le corps de l’interface utilisateur. Ils peuvent être des liens vers Help ou lancer des dialogues internes.

##### <a name="visual-style-rules-for-help-links"></a>Règles de style visuel pour les liens d’aide

- Utilisez les couleurs de l’environnement correct pour les hyperliens. Un hyperlien correctement coiffé ne clignotera pas brièvement en rouge lorsqu’il est cliqué. Si vous voyez cela, alors c’est une indication que les couleurs de l’environnement ne sont pas utilisés.

- Les soulignes ne doivent être utilisés que sur le plan stationnaire ou lorsque le lien est intégré dans un paragraphe.

- Pour plus d’informations détaillées sur les styles visuels et d’interaction pour les hyperliens, voir boutons et hyperliens.

##### <a name="writing-style-rules-for-help-links"></a>Règles de style d’écriture pour les liens d’aide

- Lors du lancement de dialogues, maintenez les normes pour les ellipses : pas d’ellipsis pour la navigation, ellipses si la tâche nécessite une interface utilisateur supplémentaire.

     ![Lien d'aide dans Visual Studio](../../extensibility/ux-guidelines/media/0601-e_helplink.png "0601-e_HelpLink")

     **Une ellipse (...) dans un lien d’aide indique que la tâche nécessitera une interface utilisateur supplémentaire.**

- Les liens ne doivent pas commencer par « Apprendre », car ce n’est pas l’intention de l’utilisateur. L’utilisateur veut répondre à une question spécifique, ne pas recevoir une éducation générale.

- Phrase aider les liens afin qu’ils posent la question que le sujet répondra.

     Incorrect: "En savoir plus sur Windows Azure Mobile Services prix"

     Correct: "Quelles options de prix sont disponibles pour Windows Azure Mobile Services?"

- N’utilisez jamais *Click...* sur le texte du lien.

- Ne jamais lier seulement le mot "ici". Ceci est problématique pour certains lecteurs d’écran, qui n’exprimera que le mot hyperlien.

     Incorrect: "Trouver des informations sur Windows Azure Mobile Services **ici**"

     Correct: "Quelles options de prix sont disponibles pour Windows Azure Mobile Services?"

- Pour plus d’informations sur le style d’écriture correct pour les liens d’aide, voir les [conseils Windows Desktop pour l’aide](/windows/desktop/uxguide/winenv-help).

#### <a name="hint-text"></a>Texte de l’astuce
 Le texte de l’indice apparaît sous forme de filigrane dans un contrôle ou en dessous du contrôle. Le formatage correct sera appliqué en utilisant le `Environment.GrayText`jeton VSColors approprié, .

 Il peut apparaître sous un certain nombre de formes.

- À la place de l’étiquette de contrôle :

     ![Texte d'indication dans Visual Studio](../../extensibility/ux-guidelines/media/0601-f_hinttext1.png "0601-f_HintText1")

- Avec un verbe, donnant des instructions:

     ![Texte d'indication dans Visual Studio](../../extensibility/ux-guidelines/media/0601-g_hinttext2.png "0601-g_HintText2")

- Avec un texte indiquant une entrée requise :

     ![Texte d'indication dans Visual Studio](../../extensibility/ux-guidelines/media/0601-h_hinttext3.png "0601-h_HintText3")

#### <a name="watermark-text"></a>Texte de filigrane
 Sur une surface de conception vide, le texte doit indiquer ce qu’il faut faire ainsi que fournir des liens pour ouvrir d’autres fenêtres connexes, le cas échéant:

 ![Texte de filigrane dans Visual Studio](../../extensibility/ux-guidelines/media/0601-i_watermarktext.png "0601-i_WatermarkText")

 **Exemple de texte filigrane dans Visual Studio**

### <a name="common-terminology"></a>Terminologie commune

|Terme|Explication|Commentaire|
|----------|-----------------|-------------|
|Connectez-vous / Signez|Verbes utilisés de façon synonyme avec le web pour représenter l’authentification dans une propriété web. Au sein des clients, nous l’utilisons autrefois comme une notion de haut niveau pour la connexion utilisateur IDE et hors, qui représente une identité de haut niveau qui fournit des capacités de haut niveau telles que l’itinérance et les licences qui ne sont pas disponibles avec toutes les autres connexions.|L’utilisateur IDE est la seule fonctionnalité qui devrait représenter un signe / signer verbe, car il représente l’utilisateur IDE de haut niveau.|
|Connectez/Déconnectez-vous|Utilisation dans les endroits où une fonctionnalité maintient une connexion unique à un service en ligne.|Server Explorer, où vous ne pouvez avoir qu’une seule connexion Azure active à la fois, est un exemple de Connect/Disconnect.|
|Ajouter / Supprimer|Non-destructeur. Utilisez lors de l’ajout ou de la suppression de quelque chose d’une liste.|Le dialogue de liste de serveur TFS Connection Manager est un exemple d’Add/Supprimer.|
|DELETE|Destructrice. Utilisez uniquement lorsque l’élément supprimé sera définitivement jeté ou supprimé du disque.|"Supprimer" nécessite généralement une invite si le résultat supprime un fichier à partir du disque.|

## <a name="error-messages"></a>Messages d’erreur

### <a name="overview"></a>Vue d'ensemble
 Des erreurs se produisent. Définir des limites sur ce que l’utilisateur peut faire est une première étape raisonnable dans la prévention des messages d’erreur évitables. Cependant, lorsqu’une erreur se produit, un message d’erreur bien écrit peut aller un long chemin vers l’atténuation du problème. Les messages d’erreur sont sans doute l’un des types de notification les plus importants que l’utilisateur voit, parce qu’ils sont synchrones et indiquent un problème qui doit être résolu. Les messages d’erreur mal écrits laissent les utilisateurs seuls décider de la cause des erreurs et de toutes les solutions possibles.

 Les utilisateurs peuvent cesser de prêter attention aux messages d’erreur surutilisés ou déroutants, alors écrivez uniquement les messages nécessaires qui ajoutent de la valeur à l’expérience utilisateur. Si le message est simplement une notification, utilisez une autre présentation.

### <a name="rules-for-creating-an-error-message"></a>Règles pour créer un message d’erreur

- Lors de la construction de messages d’erreur, choisissez le niveau d’erreur approprié pour l’audience. Visez des résumés simples qui fournissent une action que l’utilisateur peut prendre, le cas échéant. N’indiquez rien que l’utilisateur n’a pas besoin de savoir.

- Fournir une assistance constructive. Il est plus facile de lire et d’agir sur un message d’erreur qui contient des instructions.

- N’utilisez pas de double négatif.

- Effectuez à la fois une vérification automatisée et manuelle de la grammaire et de l’orthographe sur tout message d’erreur que vous écrivez.

- Pour les messages d’erreur complexes, évitez les communications séquentielles. N’utilisez jamais un branchement F1 pour le message d’erreur. Le message lui-même devrait être suffisant.

- Utilisez l’icône correcte.

- Facilitez les questions à comprendre et utilisez des boutons qui ont des choix clairs, tels que « Supprimer » et « Annuler ».

- Pour les avertissements, soyez clair sur les conséquences de la procédure. Les boutons doivent indiquer la conséquence.

- Pour les erreurs, décrivez ce que l’utilisateur peut faire pour résoudre le problème. Les boutons doivent être des actions ou dire "Fermer". N’utilisez pas de bouton "OK" pour un message d’erreur.

- Quelques questions à vous poser lors de la construction d’un message d’erreur:

  - L’utilisateur peut-il trouver comment résoudre le problème avec cette seule erreur ?

  - L’utilisateur utilise-t-il le même vocabulaire que cette erreur ?

  - Cette erreur est-elle ambigious ou partagée dans de multiples situations ? Dans l’affirmative, comment guidez-vous les utilisateurs vers la solution dont ils ont besoin ?

#### <a name="build-errors"></a>Erreurs de build
 Étant donné que Visual Studio est un outil de développement logiciel, beaucoup de ses composants ont une étape de compilation, de conversion ou d’encodage pour convertir le travail du développeur en forme binaire. Ces conversions peuvent causer des erreurs lorsque le compilateur ne peut pas traiter des fichiers mal rédigés ou lorsque les options de compilateur n’ont pas été définies correctement.

 Les utilisateurs de Visual Studio peuvent passer un nombre énorme d’heures de développement à résoudre les erreurs de construction. Ce temps de résolution augmente lorsque les erreurs ont des dépendances ou lorsque les messages d’erreur sont mal écrits, ce qui peut rendre difficile de découvrir la source de l’erreur.

 Les meilleures erreurs de construction sont celles qui ne se produisent pas en premier lieu, c’est pourquoi Visual Studio fournit AutoComplete et IntelliSense squiggles. Les validateurs de schémas et les outils similaires fournissent le même type de rétroaction. Ces mécanismes guident proactivement l’utilisateur à construire un code bien formé, ce qui réduit les risques d’erreurs de construction.

 Visual Studio fournit une fenêtre d’outil où les utilisateurs peuvent lire et naviguer à travers les erreurs qui se sont produites dans leurs fenêtres de documents. Des raccourcis clavier sont fournis afin que l’utilisateur puisse naviguer rapidement de grandes quantités de code et aller directement à l’emplacement du problème. Visual Studio permet également à chaque erreur de construire d’être liée à un mot clé d’aide particulier / ID contexte de sorte que l’utilisateur peut aller directement à un sujet d’aide qui donne des informations plus approfondies sur l’erreur.

 Écrivez des erreurs de construction claires et concises :

- **Utilisez un langage simple** qui explique le problème avec peu ou pas de jargon compilateur. Le texte d’une erreur de construction ne doit pas être trop technique.

- **Décrivez les causes possibles.** Par exemple, « Manquer un côlon entre la propriété et la valeur dans la déclaration '(propriété) : (valeur)».

- Donnez des détails sur les correctifs potentiels. S’il n’y a pas assez de place, des détails supplémentaires peuvent être mis dans le sujet d’aide correspondant.

### <a name="components-of-a-well-written-error-message"></a>Composants d’un message d’erreur bien écrit

#### <a name="use-the-shell-dialog-service-for-error-messages"></a>Utilisez le service de dialogue shell pour les messages d’erreur.
 L’utilisation du service de dialogue shell vous permet de contrôler l’apparence du message, les polices en particulier, sans modifications majeures des éléments individuels. Utilisez les mécanismes **IErrorInfo** et signalez-les à l’aide **d’IVsUIShell::SetErrorInfo/ReportErrorInfo**.

#### <a name="choose-an-effective-and-appropriate-notification-presentation"></a>Choisissez une présentation de notification efficace et appropriée.
 Utilisez un dialogue modal avec un avertissement critique si des mesures immédiates sont nécessaires pour éviter la perte de données (notification synchrone). Les icônes critiques sont réservées aux situations dans lesquelles la fermeture du message sans le lire peut entraîner des conséquences négatives. La perte de données est une situation critique qui nécessite une réponse au niveau de l’alarme. La surutilisation de l’icône critique désensibilise les utilisateurs à son importance. Si le message d’erreur est de nature informationnelle, envisagez des alternatives à un dialogue modal (notification asynchrone).

#### <a name="provide-a-clean-succinct-explanation-of-why-the-problem-occurred-rather-than-a-technical-explanation"></a>Fournir une explication propre et succincte des raisons pour lesquelles le problème s’est produit plutôt qu’une explication technique.
 Surcharger les utilisateurs avec des détails techniques dans l’explication les rendra plus susceptibles d’ignorer les messages d’erreur. Exemples de bons messages :

- "Incapable d’ouvrir le dossier demandé."

- "Incapable de se connecter à Internet."

#### <a name="provide-information-about-how-to-fix-the-problem"></a>Fournir des informations sur la façon de résoudre le problème.
 Offrez à l’utilisateur des suggestions sur la façon de résoudre le problème. Soyez honnête avec l’utilisateur s’il n’y a pas de suggestions. Fournir des liens directs vers d’autres sources en ligne, telles que le soutien technique ou le soutien communautaire. Essayez de diriger les utilisateurs vers des informations spécifiques en ligne pertinentes au problème. Pour un ID d’erreur, envisagez de relier les utilisateurs à un thread de discussion sur cette erreur spécifique. Exemples de bons messages :

- « Assurez-vous d’être connecté à Internet et d’essayer à nouveau cette opération. »

- « Assurez-vous que le fichier existe et que vous avez la permission de l’ouvrir. »

#### <a name="write-a-message-that-is-short-and-to-the-point"></a>Écrivez un message qui est court et au point.
 Un message d’erreur peut avertir, expliquer et offrir une solution, mais toujours être ignoré si elle est trop verbeuse. Une solution consiste à utiliser la divulgation progressive avec un bouton de détails. Par exemple, donnez une courte description/solution, puis mettez plus de détails sous un bouton de détails. Si les utilisateurs choisissent de lire plus d’informations sur l’erreur, ils peuvent le faire.

 La langue dans le message doit être :

- **Domaine approprié.** Utilisez un langage que l’utilisateur comprendra. Même si nos clients sont des développeurs, ils n’ont souvent pas le contexte et la terminologie que nous avons.

- **Spécifique.** Évitez les formulations vagues et donnez des noms et des emplacements spécifiques des objets impliqués. Par exemple, un message d’erreur tel que « le caractère est invalide » n’est pas utile. Quel personnage ? "Fichier non trouvé." Quel fichier ?

- **Courtois.** Ne blâmez pas l’utilisateur ou ne le faites pas se sentir stupide. Évitez les langages hostiles ou offensants (tuer, exécuter, mettre fin, fatale, illégale). Évitez le texte de la majuscule, qui est souvent considéré comme criant et n’est pas aussi lisible. N’utilise pas l’humour.

- **Correcte.** Utilisez l’orthographe et la grammaire correctes (même dans les alphas). Les typos ne sont pas professionnels et embarrassants.

- **Contextuellement approprié.** Utilisez le texte bouton approprié. Évitez le bouton "OK" et utilisez plutôt "Continuer" ou "Oui/Non".

### <a name="error-message-examples"></a>Exemples de messages d’erreur

|Bonne|Mauvaise|
|----------|---------|
|« Le numéro que vous avez composé n’est plus en service. Veuillez vérifier le numéro et composer à nouveau ou composer le 0 pour l’opérateur.|- "Erreur (449): Numéro illégal"<br />- « Cette erreur d’exception non gérée indique que l’opération s’est terminée avec succès. »<br /><br /> ![Message d'erreur incorrect dans Visual Studio](../../extensibility/ux-guidelines/media/0602-a_errordialog.png "0602-a_ErrorDialog")|

## <a name="accessing-help"></a>Accès à l'aide

### <a name="overview"></a>Vue d'ensemble
 En plus de la documentation dans MSDN, un utilisateur de Visual Studio dispose de plusieurs points d’accès pour aider l’utilisateur lors de l’interface utilisateur. Pour s’assurer que ces points d’accès sont toujours disponibles, les équipes de fonctionnalités doivent profiter du système d’aide offert par l’environnement. Ces points d’accès sont les suivants :

- **Texte pédagogique et complémentaire dans les dialogues.** Texte statique qui donne la direction ou l’explication, soit sur la surface de l’interface utilisateur ou disponible sur le plan d’une icône InfoTip.

- **F1 Aide** (éditeur seulement). Au sein de l’éditeur Visual Studio, un utilisateur peut croire qu’à tout moment, le fait de presser la F1 présentera un sujet d’aide spécifique à la sélection actuelle. Assurez-vous que les sujets associés à la F1 sont appropriés et informatifs.

- **Hyperliens pour aider les sujets.** Un lien hypertexte dans un dialogue, une fenêtre d’outils ou une surface de conception qui lance un sujet pour aider l’utilisateur à en apprendre davantage sur une technologie, une capacité ou des informations sur la façon d’accomplir une tâche.

- **Mécanismes d’interface utilisateur d’assistance, tels que les étiquettes intelligentes et les dialogues de construction.** Ces mécanismes aident l’utilisateur à comprendre un élément d’interface utilisateur, ou facilitent une tâche, comme des étiquettes intelligentes ou des dialogues de constructeur.

- **Boutons d’aide à l’interface utilisateur** (dépréciés). Un indicateur visible dans la barre de titre qui donne accès au sujet D’aide F1 connexe.

### <a name="text"></a>Texte

#### <a name="instructional-and-supplemental-text-in-dialogs"></a>Texte pédagogique et complémentaire dans les dialogues
 Dans les dialogues qui prennent en charge des tâches complexes, il pourrait être nécessaire de donner du texte pédagogique au sein de l’interface utilisateur, souvent en haut du dialogue ou des contrôles quasi complexes. Voir [le texte de l’interface utilisateur et la terminologie](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology) pour plus de détails sur le style d’écriture.

#### <a name="infotips"></a>InfoTips InfoTips
 Souvent, le texte pédagogique peut être trop long pour être positionné dans l’interface utilisateur ou peut être utile uniquement aux nouveaux utilisateurs, se sentant comme de l’encombrement pour les utilisateurs expérimentés. Dans ce cas, le texte pédagogique/informationnel doit être placé sous une pointe d’outils sous un InfoTip.

 InfoTips doit être placé près des contrôles auxquels ils sont liés et doivent utiliser l’icône spécifique InfoTip, qui est discrète mais perceptible.

 ![Info-bulle dans Visual Studio](../../extensibility/ux-guidelines/media/0601-d_infotip.png "0601-d_InfoTip")

 **Exemple d’InfoTip dans Visual Studio**

### <a name="interactive-help-mechanisms"></a>Mécanismes d’aide interactifs

#### <a name="f1-help"></a>Aide (F1)
 F1 L’aide est nécessaire dans un éditeur ou une surface de conception, mais pas ailleurs dans l’environnement Visual Studio.

#### <a name="hyperlinks-to-help-topics"></a>Hyperliens pour aider les sujets
 Les hyperliens peuvent être utilisés pour effectuer une action, naviguer dans l’IDE ou lancer Aide dans un navigateur. Voir [le texte et la terminologie de l’interface utilisateur](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology) pour plus de détails sur la langue et 07.10.01 Boutons et hyperliens pour les directives visuelles et de mise en page.

#### <a name="help--buttons-in-dialog-title-bars-deprecated"></a>Aide [?] boutons dans les barres de titre de dialogue (dépréciés)
 Pour la plupart, les boutons Help [?] dans la barre de titre des dialogues sont dépréciés. Les sujets de l’interface utilisateur ne font plus partie de notre modèle de doc, et donc il pourrait ne pas y avoir un sujet pertinent à lier. Essentiellement, le bouton barre de titre était la même chose que F1 Aide, et qui n’est plus nécessaire dans les dialogues. Dans certains cas, cela peut encore être utilisé comme un indicateur qu’il existe plus d’informations conceptuelles ou procédurales, bien que les hyperliens soient plus couramment utilisés dans les nouvelles interfaces utilisateur.

##### <a name="dialogs-created-through-the-environment"></a>Dialogues créés par l’environnement
 De nombreux dialogues de coquille sont créés grâce à la fonction **VBDialogBoxParam.** Cette fonction partagée a été mise à jour pour aider à déplacer le bouton **Aide** du dialogue à la **?** bouton tout en conservant une architecture qui est compatible vers l’arrière et extensible.

 Plus précisément, la fonction **VBDialogBoxParam** examine le modèle de dialogue pour un bouton dont l’ID est **IDHELP** (9) ou l’étiquette est **Aide** ou **&Aide**. Si un bouton Aide est trouvé, il est caché et le style **WS_EX_CONTEXTHELP** est ajouté au dialogue, qui place le **?** bouton dans la barre de titre du dialogue.

 Lorsque le dialogue est créé, il pousse le proc de dialogue sur une pile et invoque le dialogue avec un proc de dialogue pré-traitement nommé **DialogPreProc**. Quand le **?** bouton est cliqué, il envoie une **WM_SYSCOMMAND** de **SC_CONTEXTHELP** au dialogue. Le **DialogPreProc** capture cette commande et la transforme en un message **WM_HELP,** qui est transmis au proc de dialogue original.

 La plupart des dialogues créés dans l’environnement ont un bouton d’aide sur le dialogue. Lorsque le dialogue est affiché, le bouton Aide est auto-caché et seulement le **?** bouton fonctionne. Si le **?** bouton est jamais supprimé ou modifié dans Windows, cette solution vous permet de revenir rapidement aux boutons d’aide d’origine.

 Cette solution fait quatre hypothèses qui pourraient causer des bogues:

- Le bouton d’aide du dialogue est **IDHELP** (9).

- Le dialogue semble correct lorsque le bouton Aide est caché.

- Le dialogue ne remplace pas son winproc.

- Le dialogue n’est pas intégré à l’intérieur d’un autre dialogue.

  Si votre dialogue réside dans msenv et n’utilise pas **VBDialogBoxParam**, enquêter sur **l’exploitation de VBDialogBoxParam** avant de mettre en œuvre votre propre gestionnaire.

##### <a name="dialogs-created-through-other-packages"></a>Dialogues créés par d’autres paquets
 Vous pouvez implémenter votre propre solution pour les dialogues qui résident à l’extérieur msenv. Pour une classe de dialogue partagée dans votre VSPackage, envisagez de déplacer le bouton vers la barre de titre ou de mettre en œuvre un gestionnaire sur chaque dialogue. Le code suivant est un squelette d’une implémentation pour vous aider à démarrer :

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

##### <a name="help-buttons-in-managed-code"></a>Boutons d’aide dans le code géré
 Le comportement par défaut du bouton de l’aide au titre de la fenêtre est facile dans le code géré. Voici une application de démonstration complète qui démontre ce comportement. Essentiellement, vous devez remplacer la méthode **WndProc** de votre formulaire, puis renvoyer les demandes d’aide F1 lorsqu’un message **SC_CONTEXTHELP** est intercepté.

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
- [Polices et mise en forme pour Visual Studio](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md)
- [Présentation pour Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md)
- [Notifications et progression pour Visual Studio](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md)
