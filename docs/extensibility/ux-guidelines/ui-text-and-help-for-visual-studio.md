---
title: Texte de l’interface utilisateur et aide pour Visual Studio | Microsoft Docs
description: En savoir plus sur le texte et la terminologie de l’interface utilisateur utilisés dans les informations d’aide pour Visual Studio.
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: e8747d07-6c90-46cc-b425-55b589f7e9e4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 40b128c5e95c70457d92843e620b4aa072c409ba
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899431"
---
# <a name="ui-text-and-help-for-visual-studio"></a>Texte de l’interface utilisateur et Aide pour Visual Studio
## <a name="ui-text-and-terminology"></a><a name="BKMK_UITextAndTerminology"></a> Texte et terminologie de l’interface utilisateur
 Le texte compréhensible est essentiel à l’interface utilisateur efficace. Les utilisateurs de logiciels ont tendance à lire d’abord les étiquettes, à savoir celles qui sont les plus pertinentes pour effectuer la tâche en cours. Le texte statique est lu avec moins de fréquence. Planifiez les utilisateurs pour qu’ils démarrent leurs sessions de travail avec une analyse rapide de la totalité de la fenêtre, suivie d’une lecture de l’interface utilisateur dans cet ordre approximatif :

1. Contrôles interactifs au centre

2. Boutons de validation

3. Contrôles interactifs trouvés ailleurs

4. Instructions principales

5. Explications supplémentaires

6. Titre de la fenêtre

7. Autre texte statique dans le corps principal

### <a name="usage-patterns-for-ui-text"></a>Modèles d’utilisation pour le texte de l’interface utilisateur

#### <a name="title-bar-text"></a>Barre de titre Texte
 Le texte de la barre de titre doit correspondre à la commande qui a généré l’interface utilisateur.

#### <a name="instructional-text-helper-text"></a>Texte d’instructions (texte d’assistance)
 Dans certaines boîtes de dialogue, il est utile de fournir des instructions principales importantes pour expliquer ce que vous devez faire dans la fenêtre ou dans la page. Cela est parfois appelé « texte d’assistance ».

##### <a name="writing-style-rules-for-helper-text"></a>Écriture de règles de style pour le texte d’assistance

- N’Expliquez pas ce qui est évident. À moins qu’il ne soit absolument nécessaire, n’incluez pas de texte d’instructions.

- Le texte d’instructions est toujours placé en haut de la boîte de dialogue et doit faire référence à la tâche en cours d’exécution.

- Expliquez précisément aux utilisateurs ce qu’ils doivent faire. Évitez les communications et la redondance excessives.

- Passez en revue chaque fenêtre et éliminez les mots et les instructions en double.

- Conservez un texte d’instructions bref. Si des informations supplémentaires sont nécessaires pour certains utilisateurs ou scénarios, fournissez un lien vers une rubrique détaillée conceptuelle en ligne.

- Écrivez votre texte afin que chaque mot conserve le poids et soit nécessaire.

- Suivez les instructions Microsoft existantes pour le texte et le [style et le style](/windows/desktop/uxguide/text-style-tone)de l' [interface utilisateur](/windows/desktop/uxguide/text-ui) .

#### <a name="supplemental-instructions"></a>Instructions supplémentaires
 Des instructions supplémentaires fournissent des informations supplémentaires qui permettent à l’utilisateur de comprendre les contrôles ou les regroupements de contrôles. Cela peut également inclure le texte d’indication nécessaire pour comprendre le format attendu par le contrôle d’entrée. Utilisez des instructions supplémentaires avec modération. Réservez-les dans les cas où il est probable que l’utilisateur ne comprenne pas pleinement les ramifications du choix qu’il effectue.

 ![Capture d’écran montrant le bouton Options d’Internet Explorer avec un texte supplémentaire au-dessous de celui-ci, qui décrit l’impact de la modification des paramètres des options.](../../extensibility/ux-guidelines/media/0601-b_supplementaltext1.png "0601-b_SupplementalText1")

 **Texte supplémentaire dans Visual Studio**

 ![Capture d’écran de la boîte de dialogue Choisir un contrôle de code source dans Visual Studio montrant un texte supplémentaire qui décrit chacune des options du système de contrôle de code source.](../../extensibility/ux-guidelines/media/0601-c_supplementaltext2.png "0601-c_SupplementalText2")

 **Texte supplémentaire dans Visual Studio**

#### <a name="infotips"></a>Info-bulles
 Souvent, le texte d’instructions peut être trop long pour être placé sur place dans l’interface utilisateur ou peut être utile uniquement pour les nouveaux utilisateurs, ce qui s’apparente à un encombrement pour les utilisateurs expérimentés. Dans ce cas, le texte pédagogique/informatif doit être placé sous la forme d’une info-bulle sous une info-bulle.

 Info-bulles doit être placé près des contrôles auxquels il est associé et doit utiliser l’icône d’info-bulle spécifique, qui est discrète mais perceptible.

 ![Info-bulle dans Visual Studio](../../extensibility/ux-guidelines/media/0601-d_infotip.png "0601-d_InfoTip")

 **Exemple de info-bulle dans Visual Studio**

##### <a name="writing-style-rules-for-infotips"></a>Écriture de règles de style pour info-bulles

- Écrivez info-bulles en tant que phrases complètes. Elles nécessitent des verbes spécifiques, une casse des phrases et une ponctuation finale.

- Utilisez info-bulles pour compléter votre instruction principale ou vos informations. Si vous utilisez simplement des mots différents pour repenser l’idée principale, vous n’avez pas besoin d’une info-bulle.

- Gardez info-bulles Short et doux. Utilisez de petits mots et un langage quotidien ordinaire qui prend en charge et encourage l’utilisateur.

- Suivez les instructions Microsoft existantes pour le texte et le [style et le style](/windows/desktop/uxguide/text-style-tone)de l' [interface utilisateur](/windows/desktop/uxguide/text-ui) .

#### <a name="control-labels"></a>Étiquettes de contrôle
 Les étiquettes de contrôle doivent être courtes, concises et suivre les [conseils Windows Desktop pour les contrôles](/windows/desktop/uxguide/controls).

 Pour plus d’informations sur le format et l’emplacement des étiquettes de contrôle dans l’interface utilisateur, consultez [disposition pour Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md).

#### <a name="help-links"></a>Liens d’aide
 Les liens d’aide peuvent être placés dans le texte d’une instruction ou dans le corps de l’interface utilisateur. Ils peuvent être des liens permettant d’obtenir de l’aide ou de lancer des dialogues internes.

##### <a name="visual-style-rules-for-help-links"></a>Règles de style visuel pour les liens d’aide

- Utilisez les couleurs d’environnement appropriées pour les liens hypertexte. Un lien hypertexte correctement mis en forme ne clignote pas brièvement lorsque vous cliquez dessus. Si vous voyez cela, cela indique que les couleurs de l’environnement ne sont pas utilisées.

- Les traits de soulignement doivent uniquement être utilisés au pointage ou lorsque le lien est incorporé dans un paragraphe.

- Pour plus d’informations sur les styles visuels et d’interaction pour les liens hypertexte, consultez boutons et liens hypertexte.

##### <a name="writing-style-rules-for-help-links"></a>Écriture de règles de style pour les liens d’aide

- Lors du lancement de boîtes de dialogue, mettez à jour les normes pour les points de suspension : aucune Ellipse pour la navigation, ellipses si la tâche requiert une interface utilisateur supplémentaire.

     ![Lien d'aide dans Visual Studio](../../extensibility/ux-guidelines/media/0601-e_helplink.png "0601-e_HelpLink")

     **Les points de suspension (...) d’un lien d’aide indiquent que la tâche nécessite une interface utilisateur supplémentaire.**

- Les liens ne doivent pas commencer par « apprendre », car ce n’est pas l’intention de l’utilisateur. L’utilisateur souhaite répondre à une question spécifique, et ne reçoit pas de formation générale.

- Les liens d’aide de l’expression permettent de poser la question à laquelle la rubrique répond.

     Incorrect : « en savoir plus sur la tarification de Windows Azure Mobile Services »

     Correct : « Quelles sont les options de tarification disponibles pour Windows Azure Mobile Services ? »

- N’utilisez jamais *Click...* dans le texte du lien.

- Ne liez jamais le mot « ici ». Cela pose problème pour certains lecteurs d’écran, qui n’affichent que le lien hypertexte.

     Incorrect : « recherchez des informations sur Windows Azure Mobile Services **ici**»

     Correct : « Quelles sont les options de tarification disponibles pour Windows Azure Mobile Services ? »

- Pour plus d’informations sur le style d’écriture correct pour les liens d’aide, consultez le [Guide du bureau Windows pour obtenir de l’aide](/windows/desktop/uxguide/winenv-help).

#### <a name="hint-text"></a>Texte d’indication
 Le texte d’indication apparaît sous la forme d’un filigrane dans un contrôle ou sous le contrôle. La mise en forme correcte sera appliquée à l’aide du jeton VSColors approprié, `Environment.GrayText` .

 Il peut apparaître dans plusieurs formulaires.

- À la place de l’étiquette de contrôle :

     ![Capture d’écran d’un contrôle déroulant avec le texte d’indication à la place de l’étiquette de contrôle qui indique « Rechercher Explorateur de solutions (Ctrl +;) ».](../../extensibility/ux-guidelines/media/0601-f_hinttext1.png "0601-f_HintText1")

- Avec un verbe, donnant des instructions :

     ![Capture d’écran d’une zone de texte avec le texte d’indication dans le contrôle qui indique « entrez votre nom ».](../../extensibility/ux-guidelines/media/0601-g_hinttext2.png "0601-g_HintText2")

- Avec du texte indiquant une entrée obligatoire :

     ![Capture d’écran d’une zone de texte avec le texte d’indication dans le contrôle qui lit « \< requis \> ».](../../extensibility/ux-guidelines/media/0601-h_hinttext3.png "0601-h_HintText3")

#### <a name="watermark-text"></a>Texte de filigrane
 Sur une aire de conception vide, le texte doit indiquer ce qu’il faut faire et fournir des liens permettant d’ouvrir d’autres fenêtres connexes, le cas échéant :

 ![Texte de filigrane dans Visual Studio](../../extensibility/ux-guidelines/media/0601-i_watermarktext.png "0601-i_WatermarkText")

 **Exemple de texte de filigrane dans Visual Studio**

### <a name="common-terminology"></a>Terminologie courante

|Terme|Explication|Commentaire|
|----------|-----------------|-------------|
|Se connecter/se déconnecter|Les verbes utilisés sont synonymes du Web pour représenter l’authentification dans une propriété Web. Dans les clients, nous utilisons cette valeur une fois en tant que notion de niveau supérieur pour la connexion et la déconnexion de l’utilisateur de l’IDE, qui représente une identité de niveau supérieur qui fournit des fonctionnalités de niveau supérieur, telles que l’itinérance et les licences, qui ne sont pas disponibles avec toutes les autres connexions.|L’utilisateur de l’IDE est la seule fonctionnalité qui doit représenter un verbe de connexion/déconnexion, car il représente l’utilisateur IDE de niveau supérieur.|
|Se connecter/déconnecter|À utiliser dans les emplacements où une fonctionnalité gère une seule connexion à un service en ligne.|Explorateur de serveurs, où vous ne pouvez avoir qu’une seule connexion Azure active à la fois, est un exemple de connexion/déconnexion.|
|Ajouter/supprimer|Non destructif. À utiliser lors de l’ajout ou de la suppression d’éléments dans une liste.|La boîte de dialogue Liste de serveurs du gestionnaire de connexions TFS est un exemple d’ajout/suppression.|
|DELETE|Destructrice. À utiliser uniquement lorsque l’élément en cours de suppression est supprimé définitivement du disque.|« Delete » requiert généralement une invite si le résultat est la suppression d’un fichier du disque.|

## <a name="error-messages"></a>Messages d’erreur

### <a name="overview"></a>Vue d’ensemble
 Des erreurs se produisent. La définition de limitations sur ce que l’utilisateur peut faire est une première étape raisonnable pour éviter les messages d’erreur évitables. Toutefois, lorsqu’une erreur se produit, un message d’erreur bien écrit peut être long pour atténuer le problème. Les messages d’erreur sont sans doute l’un des types de notifications les plus importants que l’utilisateur voit, car ils sont synchrones et indiquent un problème qui doit être résolu. Des messages d’erreur mal écrits laissent les utilisateurs eux-mêmes pour déterminer la cause des erreurs et des solutions possibles.

 Les utilisateurs peuvent ne plus attirer l’attention sur les messages d’erreur surutilisés ou confus. par conséquent, écrivez uniquement les messages nécessaires qui ajoutent de la valeur à l’expérience utilisateur. Si le message est simplement une notification, utilisez une autre présentation.

### <a name="rules-for-creating-an-error-message"></a>Règles de création d’un message d’erreur

- Lorsque vous construisez des messages d’erreur, choisissez le niveau d’erreur approprié pour l’audience. Recherchez des résumés simples qui fournissent une action que l’utilisateur peut entreprendre, le cas échéant. N’indiquez rien que l’utilisateur n’a pas besoin de connaître.

- Fournir une assistance constructive. Il est plus facile de lire et d’agir sur un message d’erreur contenant des instructions.

- N’utilisez pas de valeurs négatives doubles.

- Effectuez une vérification automatique et grammaticale manuelle et orthographique sur tout message d’erreur que vous écrivez.

- Pour les messages d’erreur complexes, évitez les communications séquentielles. N’utilisez jamais une accroche F1 pour le message d’erreur. Le message lui-même doit être suffisant.

- Utilisez l’icône correcte.

- Facilitez la compréhension et l’utilisation des boutons qui présentent des choix clairs, tels que « supprimer » et « annuler ».

- Pour les avertissements, soyez clair sur ce qui est la conséquence de la procédure. Les boutons doivent indiquer la conséquence.

- Pour les erreurs, décrivez ce que l’utilisateur peut faire pour résoudre le problème. Les boutons doivent être des actions ou « fermer ». N’utilisez pas de bouton « OK » pour un message d’erreur.

- Voici quelques questions à vous poser lors de la création d’un message d’erreur :

  - L’utilisateur peut-il déterminer comment résoudre le problème avec cette erreur seule ?

  - L’utilisateur utilise-t-il le même vocabulaire que cette erreur ?

  - Cette erreur est-elle ambigu ou partagée dans plusieurs situations ? Si c’est le cas, comment guider les utilisateurs vers la solution dont ils ont besoin ?

#### <a name="build-errors"></a>Erreurs de build
 Étant donné que Visual Studio est un outil de développement de logiciels, un grand nombre de ses composants ont une étape de compilation, de conversion ou d’encodage pour convertir le travail du développeur au format binaire. Ces conversions peuvent provoquer des erreurs lorsque le compilateur ne peut pas traiter des fichiers créés de manière incorrecte ou lorsque les options du compilateur n’ont pas été définies correctement.

 Les utilisateurs de Visual Studio peuvent consacrer un nombre énorme d’heures de développement à la résolution des erreurs de Build. Ce temps de résolution augmente lorsque les erreurs ont des dépendances ou lorsque les messages d’erreur sont mal écrits, ce qui peut compliquer la récupération de la source de l’erreur.

 Les meilleures erreurs de build sont celles qui ne se produisent pas en premier lieu, c’est pourquoi Visual Studio fournit la saisie semi-automatique et les tildes IntelliSense. Les validateurs de schéma et les outils similaires fournissent le même type de commentaires. Ces mécanismes guident de manière proactive l’utilisateur pour construire un code correct, réduisant ainsi le risque d’erreurs de génération.

 Visual Studio fournit une fenêtre outil dans laquelle les utilisateurs peuvent lire et parcourir les erreurs qui se sont produites dans leurs fenêtres de document. Des raccourcis clavier sont fournis pour permettre à l’utilisateur de parcourir rapidement de grandes quantités de code et d’accéder directement à l’emplacement du problème. Visual Studio permet également à chaque erreur de build d’être liée à un ID de contexte/mot clé d’aide particulier afin que l’utilisateur puisse accéder directement à une rubrique d’aide qui fournit des informations plus détaillées sur l’erreur.

 Écrire des erreurs de build claires et concises :

- **Utilisez un langage simple** qui explique le problème avec peu ou pas de jargon de compilateur. Le texte d’une erreur de build ne doit pas être trop technique.

- **Structure des causes possibles.** Par exemple, « il manque un signe deux-points entre la propriété et la valeur dans la déclaration «(propriété) : (valeur) ».

- Donnez des détails sur les corrections possibles. S’il n’y a pas assez de place, des informations supplémentaires peuvent être placées dans la rubrique d’aide correspondante.

### <a name="components-of-a-well-written-error-message"></a>Composants d’un message d’erreur bien écrit

#### <a name="use-the-shell-dialog-service-for-error-messages"></a>Utilisez le service de boîte de dialogue de l’interpréteur de commandes pour les messages d’erreur.
 Le service de boîte de dialogue de l’interpréteur vous permet de contrôler l’apparence du message, en particulier les polices, sans modifications majeures apportées aux éléments individuels. Utilisez les mécanismes **IErrorInfo** et signalez-les à l’aide de **IVsUIShell :: SetErrorInfo/ReportErrorInfo**.

#### <a name="choose-an-effective-and-appropriate-notification-presentation"></a>Choisissez une présentation de notification efficace et appropriée.
 Utilisez une boîte de dialogue modale avec un avertissement critique si une action immédiate est nécessaire pour éviter la perte de données (notification synchrone). Les icônes critiques sont réservées pour les situations dans lesquelles la fermeture du message sans le lire peut entraîner des conséquences négatives. La perte de données est une situation critique nécessitant une réponse au niveau de l’alarme. L’utilisation abusive de l’icône critique désensibilisé les utilisateurs à son importance. Si le message d’erreur est de nature informatif, envisagez d’utiliser des alternatives à une boîte de dialogue modale (notification asynchrone).

#### <a name="provide-a-clean-succinct-explanation-of-why-the-problem-occurred-rather-than-a-technical-explanation"></a>Fournissez une explication claire et succincte de la raison pour laquelle le problème s’est produit plutôt qu’une explication technique.
 La surcharge des utilisateurs avec des détails techniques dans l’explication rendra plus probable l’ignorer les messages d’erreur. Exemples de bonne messagerie :

- « Impossible d’ouvrir le fichier demandé ».

- « Impossible de se connecter à Internet ».

#### <a name="provide-information-about-how-to-fix-the-problem"></a>Fournissez des informations sur la façon de résoudre le problème.
 Offrez à l’utilisateur des suggestions sur la façon de résoudre le problème. Soyez honnête avec l’utilisateur s’il n’y a pas de suggestions. Fournissez des liens directs vers d’autres sources en ligne, telles que le support technique ou le support de la communauté. Essayez de pointer les utilisateurs vers des informations en ligne spécifiques pertinentes pour le problème. Pour un ID d’erreur, envisagez de lier les utilisateurs à un thème de discussion concernant cette erreur spécifique. Exemples de bonne messagerie :

- Vérifiez que vous êtes connecté à Internet, puis recommencez l’opération.

- "Assurez-vous que le fichier existe et que vous avez l’autorisation de l’ouvrir."

#### <a name="write-a-message-that-is-short-and-to-the-point"></a>Écrivez un message bref et à un point.
 Un message d’erreur peut notifier, expliquer et proposer une solution, mais toujours être ignoré s’il est trop mot. Une solution consiste à utiliser la divulgation progressive avec un bouton Détails. Par exemple, donnez une brève description/solution, puis entrez plus de détails sous un bouton Détails. Si les utilisateurs choisissent de lire plus d’informations sur l’erreur, ils peuvent le faire.

 La langue dans le message doit être :

- **Domain-approprié.** Utilisez la langue que l’utilisateur va comprendre. Même si nos clients sont des développeurs, ils n’ont souvent pas le contexte et la terminologie dont nous disposons.

- **Plus.** Évitez les formulations vagues et attribuez des noms et des emplacements spécifiques aux objets concernés. Par exemple, un message d’erreur tel que « caractère non valide » n’est pas utile. Quel caractère ? « Fichier introuvable ». Quel fichier ?

- **Courtois.** Ne vous inquiétez pas de l’utilisateur ou ne le faites pas stupide. Évitez les langages hostiles ou choquants (Kill, Execute, Terminate, fatal, non conforme). Évitez le texte en majuscules, souvent considéré comme un crier et n’est pas aussi lisible. N’utilisez pas d’humour.

- **Correct.** Utilisez l’orthographe et la grammaire correctes (même en alpha). Les fautes de frappe ne sont pas professionnelles et ennuyeux.

- **Adapté au contexte.** Utilisez le texte du bouton approprié. Évitez le bouton « OK » et utilisez à la place « continuer » ou « oui/non ».

### <a name="error-message-examples"></a>Exemples de messages d’erreur

|Bien|Mauvaise|
|----------|---------|
|«Le numéro que vous avez composé n’est plus en service. Veuillez vérifier le numéro et composer à nouveau ou composer le numéro 0 pour l’opérateur.»|-"Error (449) : nombre non conforme"<br />-« Cette erreur d’exception non prise en charge indique que l’opération s’est terminée correctement. »<br /><br /> ![Message d'erreur incorrect dans Visual Studio](../../extensibility/ux-guidelines/media/0602-a_errordialog.png "0602-a_ErrorDialog")|

## <a name="accessing-help"></a>Accès à l'aide

### <a name="overview"></a>Vue d’ensemble
 En plus de la documentation dans MSDN, un utilisateur Visual Studio dispose de plusieurs points d’accès pour aider l’utilisateur dans l’interface utilisateur. Pour vous assurer que ces points d’accès sont disponibles de manière cohérente, les équipes de fonctionnalités doivent tirer parti du système d’aide proposé par l’environnement. Ces points d’accès sont les suivants :

- **Des instructions et du texte supplémentaire dans les boîtes de dialogue.** Texte statique qui donne un sens ou une explication, sur la surface de l’interface utilisateur ou sur une icône de pointage sur une info-bulle.

- **Aide (F1** ) (éditeur uniquement). Dans l’éditeur Visual Studio, un utilisateur peut faire confiance à cet élément à tout moment, en appuyant sur F1 pour afficher une rubrique d’aide spécifique à la sélection actuelle. Vérifiez que les rubriques associées à la touche F1 sont appropriées et informatives.

- **Liens hypertexte vers les rubriques d’aide.** Lien hypertexte dans une boîte de dialogue, une fenêtre outil ou une aire de conception qui lance une rubrique pour aider l’utilisateur à en savoir plus sur une technologie, une fonctionnalité ou des informations sur la façon d’accomplir une tâche.

- **Mécanismes d’assistance de l’interface utilisateur, tels que les balises actives et la création de boîtes de dialogue.** Ces mécanismes aident l’utilisateur à comprendre un élément d’interface utilisateur, ou à faciliter une tâche, telle que des balises actives ou des boîtes de dialogue du générateur.

- **Boutons d’aide de l’interface utilisateur** (déconseillé). Indicateur visible dans la barre de titre qui donne accès à la rubrique d’aide F1 associée.

### <a name="text"></a>Texte

#### <a name="instructional-and-supplemental-text-in-dialogs"></a>Instructions et texte supplémentaires dans les boîtes de dialogue
 Dans les boîtes de dialogue qui prennent en charge des tâches complexes, il peut être nécessaire de fournir du texte d’instructions dans l’interface utilisateur, souvent en haut de la boîte de dialogue ou des contrôles proches de la complexité. Pour plus d’informations sur l’écriture de style [, consultez texte et terminologie de l’interface utilisateur](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology) .

#### <a name="infotips"></a>Info-bulles
 Souvent, le texte d’une instruction peut être trop long pour être placé en place dans l’interface utilisateur ou peut être utile uniquement pour les nouveaux utilisateurs. Dans ce cas, le texte pédagogique/informatif doit être placé sous la forme d’une info-bulle sous une info-bulle.

 Info-bulles doit être placé près des contrôles auxquels il est associé et doit utiliser l’icône d’info-bulle spécifique, qui est discrète mais perceptible.

 ![Info-bulle dans Visual Studio](../../extensibility/ux-guidelines/media/0601-d_infotip.png "0601-d_InfoTip")

 **Exemple de info-bulle dans Visual Studio**

### <a name="interactive-help-mechanisms"></a>Mécanismes d’aide interactive

#### <a name="f1-help"></a>Aide (F1)
 L’aide (F1) est requise dans un éditeur ou une aire de conception, mais pas ailleurs dans l’environnement Visual Studio.

#### <a name="hyperlinks-to-help-topics"></a>Liens hypertexte vers les rubriques d’aide
 Les liens hypertexte peuvent être utilisés pour effectuer une action, naviguer dans l’IDE ou lancer l’aide dans un navigateur. Pour plus d’informations sur les boutons de langue et de 07.10.01 et les liens hypertexte pour obtenir des instructions visuelles et de mise en page, consultez [texte et terminologie de l’interface utilisateur](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology) .

#### <a name="help--buttons-in-dialog-title-bars-deprecated"></a>Boutons aide [ ?] dans les barres de titre de boîte de dialogue (déconseillé)
 Pour l’essentiel, les boutons aide [ ?] de la barre de titre des boîtes de dialogue sont déconseillés. Les rubriques de l’interface utilisateur ne font plus partie de notre modèle doc et, par conséquent, il se peut qu’il n’y ait pas de rubrique pertinente à lier à. Fondamentalement, le bouton de barre de titre était identique à l’aide de la touche F1 et n’est plus nécessaire dans les boîtes de dialogue. Dans certains cas, cela peut toujours être utilisé comme indicateur de disponibilité de plus en plus d’informations conceptuelles ou procédurales, bien que les liens hypertexte soient plus couramment utilisés dans une interface utilisateur plus récente.

##### <a name="dialogs-created-through-the-environment"></a>Boîtes de dialogue créées dans l’environnement
 De nombreuses boîtes de dialogue de Shell sont créées à l’aide de la fonction **VBDialogBoxParam** . Cette fonction partagée a été mise à jour pour vous aider à déplacer le bouton d' **aide** de la boîte de dialogue vers le **?** tout en conservant une architecture à compatibilité descendante et extensible.

 Plus précisément, la fonction **VBDialogBoxParam** examine le modèle de boîte de dialogue pour un bouton dont l’ID est **IDHELP** (9) ou label est **Help** ou **&aide**. Si un bouton aide est trouvé, il est masqué et le style **WS_EX_CONTEXTHELP** est ajouté à la boîte de dialogue, qui place le **?** dans la barre de titre de la boîte de dialogue.

 Quand la boîte de dialogue est créée, elle exécute un push de la procédure de dialogue sur une pile et appelle la boîte de dialogue avec une procédure de dialogue de prétraitement nommée **DialogPreProc**. Quand le **?** l’utilisateur clique sur le bouton, il envoie une **WM_SYSCOMMAND** de **SC_CONTEXTHELP** à la boîte de dialogue. Le **DialogPreProc** capture cette commande et la remplace par un message **WM_HELP** , qui est transmis à la procédure de dialogue d’origine.

 La plupart des boîtes de dialogue créées par l’environnement comportent un bouton aide dans la boîte de dialogue. Quand la boîte de dialogue s’affiche, le bouton aide est masqué automatiquement et seuls les boutons **?** le bouton fonctionne. Si le **?** le bouton n’est jamais supprimé ou modifié dans Windows. cette solution vous permet de revenir rapidement aux boutons d’aide originaux.

 Cette solution fait quatre hypothèses qui peuvent provoquer des bogues :

- Le bouton aide de la boîte de dialogue est **IDHELP** (9).

- La boîte de dialogue semble correcte lorsque le bouton aide est masqué.

- La boîte de dialogue ne remplace pas son que winproc.

- La boîte de dialogue n’est pas incorporée à l’intérieur d’une autre boîte de dialogue.

  Si votre boîte de dialogue se trouve dans msenv et n’utilise pas **VBDialogBoxParam**, étudiez l’utilisation de **VBDialogBoxParam** avant d’implémenter votre propre gestionnaire.

##### <a name="dialogs-created-through-other-packages"></a>Boîtes de dialogue créées à l’aide d’autres packages
 Vous pouvez implémenter votre propre solution pour les boîtes de dialogue qui résident en dehors de msenv. Pour une classe de dialogue partagée dans votre VSPackage, envisagez de déplacer le bouton vers la barre de titre ou d’implémenter un gestionnaire sur chaque boîte de dialogue. Le code suivant est un squelette d’implémentation pour vous aider à démarrer :

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
 La substitution du comportement par défaut du bouton d’aide de la barre de titre de la fenêtre est facile dans le code managé. Vous trouverez ci-dessous une application de démonstration complète qui illustre ce comportement. En résumé, vous devez remplacer la méthode **WndProc** de votre formulaire, puis désactiver les demandes d’aide F1 quand un message de **SC_CONTEXTHELP** est intercepté.

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
