---
title: Texte de l’interface utilisateur et l’aide de Visual Studio | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e8747d07-6c90-46cc-b425-55b589f7e9e4
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d92a8ae5d0581ae5b36276fcf857371d0ae2f8b8
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54993442"
---
# <a name="ui-text-and-help-for-visual-studio"></a>Texte de l’interface utilisateur et l’aide de Visual Studio
##  <a name="BKMK_UITextAndTerminology"></a> La terminologie et les textes d’interface utilisateur  
 Texte compréhensible est cruciale pour l’interface utilisateur efficace. Les utilisateurs de logiciels ont tendance à lire les étiquettes tout d’abord, à savoir celles les plus pertinents à l’exécution de la tâche en cours. Texte statique est en lecture avec une fréquence inférieure. Plan permettant aux utilisateurs de démarrer des sessions de leur travail avec une analyse rapide de la fenêtre entière, suivie d’une lecture de l’interface utilisateur dans cet ordre approximatif :  
  
1.  Contrôles interactifs dans le centre  
  
2.  Valider des boutons  
  
3.  Contrôles interactifs trouvées ailleurs  
  
4.  Instructions principales  
  
5.  Obtenir des explications supplémentaires  
  
6.  Titre de la fenêtre  
  
7.  Tout autre texte statique dans le corps principal  
  
### <a name="usage-patterns-for-ui-text"></a>Modèles d’utilisation pour le texte de l’interface utilisateur  
  
#### <a name="title-bar-text"></a>Texte de barre de titre  
 Texte de barre de titre doit correspondre à la commande qui a généré l’interface utilisateur.  
  
#### <a name="instructional-text-helper-text"></a>Texte d’instructions (texte d’assistance)  
 Dans certaines boîtes de dialogue, il est utile de fournir les principales instructions principales pour expliquer que faire dans la fenêtre ou dans la page. Cela est parfois appelé « texte d’assistance ».  
  
##### <a name="writing-style-rules-for-helper-text"></a>Écriture de règles de style pour le texte d’aide  
  
-   N’expliquent pas les évidents. Sauf si elle est absolument nécessaire, n’incluez pas le texte d’instructions.  
  
-   Texte d’instructions est toujours placé en haut de la boîte de dialogue et doit faire référence à la tâche en cours d’exécution.  
  
-   Expliquer précisément aux utilisateurs qu’ils doivent faire. Éviter la redondance et la communication excessive.  
  
-   Passez en revue chaque fenêtre et éliminer les instructions et les mots en double.  
  
-   Conserver le texte d’instructions court. Si plus d’informations est nécessaire pour certains utilisateurs ou scénarios, indiquez un lien vers une rubrique en ligne conceptuelle détaillée.  
  
-   Écrivez votre texte afin que chaque mot conserve le poids et n’est nécessaire.  
  
-   Suivez les conseils de Microsoft existant pour [texte de l’Interface utilisateur](/windows/desktop/uxguide/text-ui) et [Style et le ton](/windows/desktop/uxguide/text-style-tone).  
  
#### <a name="supplemental-instructions"></a>Obtenir des instructions supplémentaires  
 Obtenir des instructions supplémentaires fournissent des informations supplémentaires qui aide l’utilisateur à comprendre les contrôles ou de contrôler les regroupements. Cela peut également inclure le texte d’indication nécessaire pour comprendre quel format le contrôle d’entrée est attendu. Utilisez des instructions supplémentaires avec parcimonie. Les réserver pour les cas où il est probable que l’utilisateur ne comprenez pleinement les conséquences du choix qu’ils font.  
  
 ![Texte supplémentaire dans Visual Studio](../../extensibility/ux-guidelines/media/0601-b_supplementaltext1.png "0601-b_SupplementalText1")  
  
 **Texte supplémentaire dans Visual Studio**  
  
 ![Texte supplémentaire dans Visual Studio](../../extensibility/ux-guidelines/media/0601-c_supplementaltext2.png "0601-c_SupplementalText2")  
  
 **Texte supplémentaire dans Visual Studio**  
  
#### <a name="infotips"></a>Info-bulles  
 Souvent, le texte d’instructions est peut-être trop long pour positionner sur place dans l’interface utilisateur ou peut être utile uniquement aux nouveaux utilisateurs, une sensation encombrement aux utilisateurs expérimentés. Dans ce cas, le texte d’instructions / d’information doit être placé comme une info-bulle sous une info-bulle.  
  
 Info-bulle doit être placé à proximité des contrôles qu’ils sont liés à et doivent utiliser l’icône d’info-bulle spécifique, qui est encore discrète notable.  
  
 ![Info-bulle dans Visual Studio](../../extensibility/ux-guidelines/media/0601-d_infotip.png "0601-d_InfoTip")  
  
 **Exemple d’une info-bulle dans Visual Studio**  
  
##### <a name="writing-style-rules-for-infotips"></a>Règles de style d’écriture pour les info-bulles  
  
-   Écrire des info-bulles sous forme de phrases complètes. Ils nécessitent des verbes spécifiques, le cas de phrase et la ponctuation de fin.  
  
-   Utilisez des info-bulles pour compléter votre instruction principale ou des informations. Si vous utilisez simplement les différents mots de retraiter l’idée principale, vous n’avez pas besoin une info-bulle.  
  
-   Conserver les info-bulles bref et concis. Utiliser des petits mots et brut, en langage naturel qui prend en charge et encourage l’utilisateur.  
  
-   Suivez les conseils de Microsoft existant pour [texte de l’Interface utilisateur](/windows/desktop/uxguide/text-ui) et [Style et le ton](/windows/desktop/uxguide/text-style-tone).  
  
#### <a name="control-labels"></a>Étiquettes de contrôle  
 Étiquettes de contrôle doivent être court et concise, suivez le [des conseils de bureau de Windows pour les contrôles](/windows/desktop/uxguide/controls).  
  
 Pour plus d’informations sur le format d’étiquette de contrôle et de placement au sein de l’interface utilisateur, consultez [Layout for Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md).  
  
#### <a name="help-links"></a>Liens d’aide  
 Liens d’aide peuvent soit être placés dans le texte d’instructions ou dans le corps de l’interface utilisateur. Ils peuvent être des liens vers l’aide ou lancez l’internes boîtes de dialogue.  
  
##### <a name="visual-style-rules-for-help-links"></a>Règles de style visuel pour les liens d’aide  
  
-   Utiliser les couleurs de l’environnement approprié pour les liens hypertexte. Un lien hypertexte correctement stylé pas brièvement clignote en rouge lorsque vous cliquez sur. Si vous le voir, il est une indication que les couleurs de l’environnement ne sont pas utilisés.  
  
-   Soulignements doivent uniquement être utilisées sur pointage ou lorsque le lien est incorporé dans un paragraphe.  
  
-   Pour obtenir des informations plus détaillées sur les styles visuels et l’interaction des liens hypertexte, consultez les boutons et des liens hypertexte.  
  
##### <a name="writing-style-rules-for-help-links"></a>Écriture de règles de style pour les liens d’aide  
  
-   Lors du lancement de boîtes de dialogue, mettre à jour les normes pour les points de suspension : aucun bouton de sélection pour la navigation, si la tâche requiert une interface utilisateur supplémentaire des points de suspension.  
  
     ![Lien d’aide dans Visual Studio](../../extensibility/ux-guidelines/media/0601-e_helplink.png "0601-e_HelpLink")  
  
     **Points de suspension (...) dans un lien d’aide indique que la tâche nécessite une interface utilisateur supplémentaire.**  
  
-   Liens ne doivent pas commencer par « Apprentissage », car il se n'agit pas d’intention de l’utilisateur. L’utilisateur souhaite répondre à une question spécifique, pas recevoir une formation générale.  
  
-   Les liens d’aide d’une expression afin qu’ils poser la question que la rubrique répondra.  
  
     Incorrect :  
     « En savoir plus sur la tarification Windows Azure Mobile Services »  
  
     Corriger :  
     « Quelles options de tarification sont disponibles pour Windows Azure Mobile Services ? »  
  
-   N’utilisez jamais *cliquez sur...*  pour le texte du lien.  
  
-   Ne jamais lier uniquement le mot « ici ». Cela peut être problématique pour certains lecteurs d’écran, qui seront vocal uniquement le lien hypertexte mot.  
  
     Incorrect :  
     « Rechercher des informations sur Windows Azure Mobile Services **ici**»  
  
     Corriger :  
     « Quelles options de tarification sont disponibles pour Windows Azure Mobile Services ? »  
  
-   Pour plus d’informations sur le style rédactionnel correct pour les liens d’aide, consultez le [conseils Windows Desktop aide](/windows/desktop/uxguide/winenv-help).  
  
#### <a name="hint-text"></a>Texte d’indication  
 Texte d’indication apparaît en filigrane dans un contrôle ou sous le contrôle. Mise en forme correcte s’appliquera à l’aide du jeton VSColors approprié, `Environment.GrayText`.  
  
 Elle peut apparaître dans plusieurs formes.  
  
-   À la place de l’étiquette de contrôle :  
  
     ![Indicateur de texte dans Visual Studio](../../extensibility/ux-guidelines/media/0601-f_hinttext1.png "0601-f_HintText1")  
  
-   Avec un verbe, ce qui donne des instructions :  
  
     ![Indicateur de texte dans Visual Studio](../../extensibility/ux-guidelines/media/0601-g_hinttext2.png "0601-g_HintText2")  
  
-   Avec le texte qui indique une entrée requise :  
  
     ![Indicateur de texte dans Visual Studio](../../extensibility/ux-guidelines/media/0601-h_hinttext3.png "0601-h_HintText3")  
  
#### <a name="watermark-text"></a>Texte de filigrane  
 Sur une aire de conception vide, le texte doit indiquer ce qu’il faut effectuer ainsi que de fournir des liens pour ouvrir d’autres fenêtres associées, le cas échéant :  
  
 ![Un texte dans Visual Studio en filigrane](../../extensibility/ux-guidelines/media/0601-i_watermarktext.png "0601-i_WatermarkText")  
  
 **Exemple de texte de filigrane dans Visual Studio**  
  
### <a name="common-terminology"></a>Terminologie courante  
  
|Terme|Explication|Commentaire|  
|----------|-----------------|-------------|  
|Se connecter / déconnecter|Verbes utilisés indifféremment avec le web pour représenter l’authentification dans une propriété web. Dans les clients, nous utilisons cette fois comme une notion de niveau supérieur pour la signature dans et hors connexion d’utilisateur de l’IDE, ce qui représente une identité de niveau supérieur qui fournit des fonctionnalités de niveau supérieur tels que l’itinérance et de gestion des licences qui ne sont pas disponibles avec toutes les autres connexions.|L’utilisateur de l’IDE est la seule fonctionnalité qui doit représenter une connexion / déconnexion verbe, car il représente l’utilisateur IDE de niveau supérieur.|  
|Connecter / déconnecter|Utiliser dans des lieux où une fonctionnalité conserve une connexion unique à un service en ligne.|Explorateur de serveurs, où vous ne pouvez avoir qu’une seule connexion d’Azure active à la fois, est un exemple de connecter/déconnecter.|  
|Ajouter / supprimer|Non destructif. À utiliser lorsque l’ajout ou la suppression d’éléments dans une liste.|La boîte de dialogue Gestionnaire de connexions TFS server liste est un exemple d’ajout/suppression.|  
|Supprimer|Destructeur. Utilisez uniquement lorsque l’élément en cours de suppression est définitivement rejeté ou supprimé à partir du disque.|« Supprimer » requiert généralement une invite si le résultat est si vous supprimez un fichier de disque.|  
  
## <a name="error-messages"></a>Messages d’erreur  
  
### <a name="overview"></a>Vue d'ensemble  
 Des erreurs se produisent. Définition des limitations sur l’utilisateur peut effectuer est une première étape à empêcher les messages d’erreur évitable raisonnable. Toutefois, lorsqu’une erreur se produit, un message d’erreur bien écrite peut accéder un long chemin pour atténuer le problème. Messages d’erreur sont sans doute un des types plus importants de notification que l’utilisateur voit, parce qu’ils sont synchrones et indiquent un problème qui doit être résolu. Messages d’erreur mal écrit laissent les utilisateurs sur leurs propres pour déterminer la cause des erreurs et les solutions possibles.  
  
 Les utilisateurs peut s’arrêter en faisant attention à l’utilisation excessive ou confusion entre les messages d’erreur, afin de l’expérience de l’écriture des messages uniquement nécessaires valeur ajoutée à l’utilisateur. Si le message est simplement une notification, puis utiliser une autre présentation.  
  
### <a name="rules-for-creating-an-error-message"></a>Règles de création d’un message d’erreur  
  
-   Lors de la construction de messages d’erreur, choisissez le niveau d’erreur approprié pour le public. L’objectif est de résumés simples qui fournissent une action à que l’utilisateur peut exécuter, le cas échéant. État de ne pas tout ce que l’utilisateur n’a pas besoin de connaître.  
  
-   Fournir une assistance constructif. Il est plus facile à lire et agir sur un message d’erreur qui contient l’instruction.  
  
-   N’utilisez pas deux négatifs.  
  
-   Effectuer les deux un moyen automatisé et manuel grammaire et l’orthographe vérifier sur n’importe quel message d’erreur que vous écrivez.  
  
-   Pour les messages d’erreur complexes, évitez de communications séquentielles. N’utilisez jamais une accroche F1 pour le message d’erreur. Le message lui-même doit être suffisant.  
  
-   Utilisez l’icône correcte.  
  
-   Formuler des questions faciles à comprendre et utiliser les boutons qui ont un choix clair, tels que « Supprimer » et « Annuler ».  
  
-   Pour les avertissements, être clair sur ce que sera la conséquence de continuer. Les boutons doivent indiquer la conséquence.  
  
-   Pour les erreurs, décrivent ce que l’utilisateur peut faire pour résoudre le problème. Boutons doivent être des actions ou dire « Fermer ». N’utilisez pas un bouton « OK » pour un message d’erreur.  
  
-   Quelques questions à poser lors de la construction d’un message d’erreur :  
  
    -   L’utilisateur vous rendiez compte comment résoudre le problème avec cette erreur autonome ?  
  
    -   L’utilisateur utilise-t-elle le vocabulaire de même que cette erreur ?  
  
    -   Est ambigu de cette erreur, ou partagés dans plusieurs situations ? Dans ce cas, comment vous guident les utilisateurs à la solution que dont ils ont besoin ?  
  
#### <a name="build-errors"></a>Erreurs de build  
 Dans la mesure où Visual Studio est un outil de développement logiciel, la plupart de ses composants ont une compilation, la conversion ou encodage étape pour convertir le travail du développeur sous forme binaire. Ces conversions peuvent provoquer des erreurs lorsque le compilateur ne peut pas traiter les fichiers créés de manière incorrecte ou lorsque les options du compilateur n’ont pas été correctement définies.  
  
 Utilisateurs de Visual Studio peuvent passer une quantité énorme de résolution des erreurs de build d’heures de développement. Ce délai de résolution augmente lorsque les erreurs ont des dépendances ou lorsque les messages d’erreur sont mal écrit, ce qui peut rendre difficile de découvrir la source de l’erreur.  
  
 Des erreurs de build sont ceux qui ne se produisent pas dans le premier lieu, c’est pourquoi Visual Studio fournit la saisie semi-automatique et IntelliSense tildes. Validateurs de schéma et des outils similaires fournissent le même type de commentaires. Ces mécanismes guident proactivement l’utilisateur pour construire un code bien formé, réduisant le risque d’erreurs de build.  
  
 Visual Studio fournit une fenêtre outil où les utilisateurs peuvent lire et parcourir les erreurs qui se sont produites dans leur fenêtre de document. Raccourcis clavier sont fournis pour que l’utilisateur peut naviguer rapidement grandes quantités de code et accéder directement à l’emplacement du problème. Visual Studio permet également de chaque erreur de build d’être associé à un ID de mot clé/contexte d’aide particulier, afin que l’utilisateur peut accéder directement à une rubrique d’aide qui donne des informations plus détaillées sur l’erreur.  
  
 Écrire les erreurs de build clairs et concis :  
  
-   **Utiliser un langage simple** qui explique le problème avec peu ou pas jargon du compilateur. Le texte d’une erreur de build ne doit pas être trop technique.  
  
-   **Décrit les causes possibles.** Par exemple, « manque un signe deux-points entre la propriété et la valeur dans le ' (propriété) : (valeur)' déclaration. »  
  
-   Fournissez des détails sur les corrections éventuelles. Si l’espace n’est pas suffisant, des détails supplémentaires peuvent être mis dans la rubrique d’aide correspondante.  
  
### <a name="components-of-a-well-written-error-message"></a>Composants d’un message d’erreur bien écrits  
  
#### <a name="use-the-shell-dialog-service-for-error-messages"></a>Utiliser le service de boîte de dialogue d’interpréteur de commandes pour les messages d’erreur.  
 L’utilisation du service de boîte de dialogue d’interpréteur de commandes vous permet de contrôler l’apparence du message, polices, en particulier, sans modification majeure aux éléments individuels. Utilisez le **IErrorInfo** mécanismes et les signaler à l’aide de **IVsUIShell::SetErrorInfo/ReportErrorInfo**.  
  
#### <a name="choose-an-effective-and-appropriate-notification-presentation"></a>Choisir une présentation de notification efficaces et appropriés.  
 Utilisez la boîte de dialogue modale avec un avertissement critique si une action immédiate est nécessaire pour éviter une perte de données (notification synchrone). Icônes critiques sont réservés pour les situations dans le message sans effectuer de lecture de fermeture, cela peut entraîner des conséquences négatives. Perte de données est une situation critique qui nécessite une réponse au niveau de l’alarme. Utilisation excessive de l’icône critique desensitizes aux utilisateurs de son importance. Si le message d’erreur est de nature informationnelle, prendre en compte les alternatives à la boîte de dialogue modale (notification asynchrone).  
  
#### <a name="provide-a-clean-succinct-explanation-of-why-the-problem-occurred-rather-than-a-technical-explanation"></a>Fournir une explication de nette et succincte de la cause du problème au lieu d’obtenir une explication technique.  
 Surcharger les utilisateurs avec des détails techniques dans l’explication rend les plus susceptibles d’ignorer les messages d’erreur. Exemples de bon de messagerie :  
  
-   « Impossible d’ouvrir le fichier demandé. »  
  
-   « Impossible de se connecter à Internet. »  
  
#### <a name="provide-information-about-how-to-fix-the-problem"></a>Fournissent des informations sur la façon de résoudre le problème.  
 Des suggestions l’utilisateur pour résoudre le problème. Être honnêtes avec l’utilisateur s’il en existe aucune suggestion. Fournir des liens directs vers les autres sources en ligne, telles que le support technique ou le support de la Communauté. Essayez dirigent les utilisateurs vers des informations en ligne spécifiques pertinentes pour le problème. Pour un ID d’erreur, envisagez de lier des utilisateurs à un thread de discussion sur l’erreur concernée. Exemples de bon de messagerie :  
  
-   « Vérifiez que vous êtes connecté à Internet et recommencez l’opération. »  
  
-   « Vérifiez que le fichier existe et que vous êtes autorisé à ouvrir. »  
  
#### <a name="write-a-message-that-is-short-and-to-the-point"></a>Écrire un message qui est à court et au point.  
 Un message d’erreur peut notifier, expliquer et offrir une solution, mais toujours être ignorée si elle est trop longue. Une solution consiste à utiliser l’affichage progressif avec un bouton Détails. Par exemple, donner une courte description/solution, puis entrer plus de détails sous un bouton Détails. Si les utilisateurs choisissent d’en savoir plus sur l’erreur, il peuvent le faire.  
  
 La langue dans le message doit être :  
  
-   **Domaine approprié.** Utiliser le langage de que l’utilisateur comprenne. Bien que nos clients sont des développeurs, ils n’ont souvent le contexte et la terminologie que nous avons.  
  
-   **Spécifique.** Évitez les vagues libellé et donner des noms spécifiques et les emplacements des objets impliqués. Par exemple, un message d’erreur tels que « le caractère non valide » n’est pas utile. Le caractère ? « Fichier introuvable ». Quel fichier ?  
  
-   **Courtoise.** Ne pas rendre responsable de l’utilisateur ou Rabaissez. Éviter de langage hostile ou offensant (arrêter, exécuter, arrêter, irrécupérable, non conforme). Évitez le texte en majuscules, ce qui est souvent considéré comme trouver et n’est pas comme lisible. N’utilisez pas humour.  
  
-   **Correct.** Utilisation correcte de grammaire et orthographe (même prémultipliés). Fautes de frappe sont non professionnelle et ennuyeux.  
  
-   **En fonction du contexte approprié.** Utilisez le texte du bouton approprié. Éviter le bouton « OK » et à la place utiliser « Continuer » ou « Yes/No ».  
  
### <a name="error-message-examples"></a>Exemples de messages d’erreur  
  
|Bon|incorrecte|  
|----------|---------|  
|« Le nombre que vous avez composé est retiré du service. Veuillez vérifier le numéro et recomposer ou composez le 0 pour l’opérateur. »|-« Erreur (449) : Nombre non conforme »<br />-« Cette erreur d’exception non gérée indique que l’opération a réussi. »<br /><br /> ![Message d’erreur incorrect dans Visual Studio](../../extensibility/ux-guidelines/media/0602-a_errordialog.png "0602-a_ErrorDialog")|  
  
## <a name="accessing-help"></a>Accéder à l’aide  
  
### <a name="overview"></a>Vue d'ensemble  
 En plus de documentation dans MSDN, un utilisateur de Visual Studio a plusieurs points d’accès pour aider l’utilisateur dans l’interface utilisateur. Pour vous assurer que ces points d’accès sont constamment disponibles, les équipes fonctionnelles doivent tirer parti du système d’aide proposé par l’environnement. Ces points d’accès sont :  
  
-   **Texte pédagogique et supplémentaire dans les boîtes de dialogue.** Texte statique qui donne une direction ou explication, soit sur l’interface utilisateur de surface ou disponible sur le pointage sur une icône d’info-bulle.  
  
-   **Aide (F1)** (éditeur uniquement). Dans l’éditeur Visual Studio, un utilisateur peut faire confiance qu’à tout moment, en appuyant sur F1 fera apparaître une rubrique d’aide spécifique à la sélection actuelle. Assurez-vous que les rubriques associées F1 sont appropriées et informatifs.  
  
-   **Liens hypertexte vers des rubriques d’aide.** Un lien hypertexte dans une boîte de dialogue, une fenêtre outil ou une aire de conception qui lance une rubrique pour aider l’utilisateur en savoir plus sur une technologie, fonctionnalité ou d’informations sur la façon d’accomplir une tâche.  
  
-   **Mécanismes de l’interface utilisateur d’assistance, telles que les balises actives et les boîtes de dialogue de création.** Ces mécanismes aider l’utilisateur à comprendre un élément d’interface utilisateur ou facilitent une tâche, telle que les balises actives ou des boîtes de dialogue Générateur de rapports.  
  
-   **Boutons d’aide de l’interface utilisateur** (déconseillé). Un indicateur visible dans la barre de titre qui donne accès à la rubrique d’aide (F1) associée.  
  
### <a name="text"></a>Texte  
  
#### <a name="instructional-and-supplemental-text-in-dialogs"></a>Texte pédagogique et supplémentaire dans les boîtes de dialogue  
 Dans les boîtes de dialogue qui prennent en charge des tâches complexes, il peut être nécessaire de donner à texte d’instructions au sein de l’interface utilisateur, souvent en haut de la boîte de dialogue ou à proximité des contrôles complexes. Consultez [l’interface utilisateur texte et la terminologie](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology) pour plus d’informations sur l’écriture de style.  
  
#### <a name="infotips"></a>Info-bulles  
 Souvent, un texte d’instructions est peut-être trop long pour positionner en place dans l’interface utilisateur ou peut être utile uniquement aux nouveaux utilisateurs, l’encombrement aux utilisateurs expérimentés une sensation. Dans ce cas, le texte d’instructions / d’information doit être placé comme une info-bulle sous une info-bulle.  
  
 Info-bulle doit être placé à proximité des contrôles qu’ils sont liés à et doivent utiliser l’icône d’info-bulle spécifique, qui est encore discrète notable.  
  
 ![Info-bulle dans Visual Studio](../../extensibility/ux-guidelines/media/0601-d_infotip.png "0601-d_InfoTip")  
  
 **Exemple d’une info-bulle dans Visual Studio**  
  
### <a name="interactive-help-mechanisms"></a>Mécanismes d’aide interactives  
  
#### <a name="f1-help"></a>F1 Aide  
 Aide (F1) est requis dans un éditeur ou l’aire de conception, mais pas ailleurs dans l’environnement Visual Studio.  
  
#### <a name="hyperlinks-to-help-topics"></a>Liens hypertexte vers des rubriques d’aide  
 Liens hypertexte peuvent être utilisés pour effectuer une action, naviguer dans l’IDE ou lancer l’aide dans un navigateur. Consultez [l’interface utilisateur texte et la terminologie](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology) pour plus d’informations sur le langage et 07.10.01 boutons et des liens hypertexte pour obtenir des instructions visuel et de mise en page.  
  
#### <a name="help--buttons-in-dialog-title-bars-deprecated"></a>Aide des boutons [ ?] dans les barres de titre de boîte de dialogue (déconseillées)  
 La plupart du temps, les boutons d’aide [ ?] dans la barre de titre des boîtes de dialogue sont déconseillés. Rubriques de l’interface utilisateur ne font plus partie de notre modèle de document, et par conséquent, il peut revêtir une rubrique appropriée à lier à. Essentiellement, le bouton de barre de titre a été la même chose que la touche F1, et qui n’est plus nécessaire dans les boîtes de dialogue. Dans certains cas, cela peut toujours être utilisée comme un indicateur que plus d’informations conceptuelles ou de procédures est disponible, bien que les liens hypertexte sont plus couramment utilisés dans l’interface utilisateur plus récente.  
  
##### <a name="dialogs-created-through-the-environment"></a>Boîtes de dialogue créées par l’environnement.  
 Nombreuses boîtes de dialogue shell sont créés via le **VBDialogBoxParam** (fonction). Cette fonction partagée a été mis à jour pour aider lors du déplacement de la **aide** bouton à partir de la boîte de dialogue le **?** bouton tout en conservant une architecture en amont compatible et extensible.  
  
 Plus précisément, le **VBDialogBoxParam** fonction examine le modèle de boîte de dialogue pour un bouton dont l’ID est **IDHELP** (9) ou de l’étiquette est **aide** ou **& aide**. Si un bouton aide est trouvé, il est masqué et le **WS_EX_CONTEXTHELP** style est ajouté à la boîte de dialogue, ce qui place le **?** bouton dans la barre de titre de la boîte de dialogue.  
  
 Quand la boîte de dialogue est créée, elle exécute un push de la procédure de boîte de dialogue dans une pile et appelle la boîte de dialogue avec une procédure de boîte de dialogue pré-traitement nommée **DialogPreProc**. Lorsque le **?** bouton est activé, il envoie un **WM_SYSCOMMAND** de **SC_CONTEXTHELP** à la boîte de dialogue. Le **DialogPreProc** capture cette commande et la remplace par une **WM_HELP** message, qui est passé à la procédure de boîte de dialogue d’origine.  
  
 La plupart des boîtes de dialogue environnement créé ont un bouton d’aide sur la boîte de dialogue. Lorsque la boîte de dialogue s’affiche, le bouton aide est masquée automatiquement et uniquement le **?** fonctionnement du bouton. Si le **?** bouton est jamais supprimé ou modifié dans Windows, cette solution vous permet de ramener rapidement vers les boutons d’aide d’origine.  
  
 Cette solution sur les hypothèses quatre qui pourrait provoquer des bogues :  
  
- Bouton d’aide de la boîte de dialogue est **IDHELP** (9).  
  
- La boîte de dialogue semble correcte lorsque le bouton aide est masqué.  
  
- La boîte de dialogue ne remplace pas sa fonction winproc.  
  
- La boîte de dialogue n’est pas incorporé à l’intérieur d’une autre boîte de dialogue.  
  
  Si votre boîte de dialogue se trouve dans msenv et n’utilise pas **VBDialogBoxParam**, parti **VBDialogBoxParam** avant d’implémenter votre propre gestionnaire.  
  
##### <a name="dialogs-created-through-other-packages"></a>Boîtes de dialogue créées via d’autres packages  
 Vous pouvez implémenter votre propre solution pour les boîtes de dialogue qui résident en dehors de msenv. Pour une classe de boîte de dialogue partagé dans votre VSPackage, envisagez de déplacer le bouton à la barre de titre ou l’implémentation d’un gestionnaire sur chaque boîte de dialogue. Le code suivant est un squelette d’une implémentation pour vous aider à bien démarrer :  
  
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
 Il suffit de substituer le comportement par défaut de la fenêtre titre barre aide du bouton dans le code managé. Voici une application de démonstration complet qui illustre ce comportement. En bref, vous devez remplacer votre formulaire **WndProc** (méthode) et les incendies puis désactiver F1 Aide demandes quand un **SC_CONTEXTHELP** message est intercepté.  
  
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
 [Polices et mise en forme pour Visual Studio](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md)   
 [Mise en page pour Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md)   
 [Notifications et progression pour Visual Studio](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md)