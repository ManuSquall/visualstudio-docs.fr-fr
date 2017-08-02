---
title: "Texte de l&#39;interface utilisateur et l&#39;aide de Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e8747d07-6c90-46cc-b425-55b589f7e9e4
caps.latest.revision: 2
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 2
---
# Texte de l&#39;interface utilisateur et l&#39;aide de Visual Studio
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

##  <a name="BKMK_UITextAndTerminology"></a> Texte de l'interface utilisateur et la terminologie  
 Texte compréhensible est cruciale pour l'interface utilisateur efficace. Les utilisateurs de logiciels ont tendance à lire les étiquettes tout d'abord, à savoir celles adaptées à la fin de la tâche en cours. Lecture du texte statique avec moins de fréquence. Plan pour les utilisateurs à démarrer leurs sessions de travail avec une analyse rapide de l'intégralité de la fenêtre, suivie d'une lecture de l'interface utilisateur dans cet ordre approximatif :  
  
1.  Contrôles interactifs dans le centre  
  
2.  Valider des boutons  
  
3.  Contrôles interactifs trouvées ailleurs  
  
4.  Instructions principales  
  
5.  Explications supplémentaires  
  
6.  Titre de la fenêtre  
  
7.  Tout autre texte statique dans le corps principal  
  
### Modèles d'utilisation pour le texte de l'interface utilisateur  
  
#### Texte de barre de titre  
 Texte de barre de titre doit correspondre à la commande qui a généré l'interface utilisateur.  
  
#### Texte d'instructions \(texte d'aide\)  
 Dans certaines boîtes de dialogue, il est utile fournir des instructions principales en cas d'expliquer comment procéder dans la fenêtre ou dans la page. Cela est parfois appelé « texte d'aide. »  
  
##### Écrire des règles de style pour le texte d'aide  
  
-   Ne pas expliquer l'évident. Sauf si cela est absolument nécessaire, n'incluez pas le texte d'instructions.  
  
-   Texte d'instructions est toujours placé en haut de la boîte de dialogue et doit faire référence à la tâche en cours d'exécution.  
  
-   Expliquez précisément aux utilisateurs qu'ils doivent faire. Éviter la redondance et la communication excessive.  
  
-   Passez en revue chaque fenêtre et éliminer les instructions et les mots en double.  
  
-   Conserver le court texte d'instructions. Si plus d'informations est nécessaire pour certains utilisateurs ou scénarios, indiquez un lien vers une rubrique en ligne conceptuel détaillée.  
  
-   Écrivez votre texte afin que chaque mot conserve le poids et n'est nécessaire.  
  
-   Suivez les conseils de Microsoft existant [texte de l'Interface utilisateur](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742478\(v=vs.85\).aspx) et [Style et ton](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742477\(v=vs.85\).aspx).  
  
#### Instructions supplémentaires  
 Des instructions supplémentaires fournissent des informations supplémentaires qui aide l'utilisateur à comprendre des contrôles ou des regroupements de contrôle. Cela peut également inclure le texte d'indication nécessaire de comprendre le format utilisé par le contrôle d'entrée est attendue. Suivez les instructions supplémentaires avec parcimonie. Réserver aux cas où il est probable que l'utilisateur ne sont pas apprécier pleinement les ramifications du choix qu'ils font.  
  
 ![Supplemental text in Visual Studio](../../extensibility/ux-guidelines/media/0601-b_supplementaltext1.png "0601\-b\_SupplementalText1")  
  
 **Texte supplémentaire dans Visual Studio**  
  
 ![Supplemental text in Visual Studio](~/extensibility/ux-guidelines/media/0601-c_supplementaltext2.png "0601\-c\_SupplementalText2")  
  
 **Texte supplémentaire dans Visual Studio**  
  
#### Info\-bulles  
 Souvent, le texte peut être trop long pour positionner sur place dans l'interface utilisateur ou peut être utile uniquement aux nouveaux utilisateurs une sensation encombrement aux utilisateurs expérimentés. Dans ce cas, le texte démonstration \/ d'information doit être placé comme une info\-bulle dans une info\-bulle.  
  
 Info\-bulles doivent être placés près les contrôles qu'ils concernent et doivent utiliser l'icône d'info\-bulle spécifique, qui n'est pas discrète notable.  
  
 ![InfoTip in Visual Studio](../../extensibility/ux-guidelines/media/0601-d_infotip.png "0601\-d\_InfoTip")  
  
 **Exemple d'une info\-bulle dans Visual Studio**  
  
##### Règles de style d'écriture pour les info\-bulles  
  
-   Écrire des info\-bulles sous forme de phrases. Ils nécessitent des verbes spécifiques, casse et ponctuation de fin.  
  
-   Utiliser des info\-bulles pour compléter votre instruction principale ou les informations. Si vous utilisez uniquement des mots différents pour redéfinir l'idée principale, vous n'avez pas besoin une info\-bulle.  
  
-   Conserver les info\-bulles bref. Utiliser des mots petit et brut, langage courant qui prend en charge et encourage l'utilisateur.  
  
-   Suivez les conseils de Microsoft existant [texte de l'Interface utilisateur](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742478\(v=vs.85\).aspx) et [Style et ton](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742477\(v=vs.85\).aspx).  
  
#### Étiquettes de contrôle  
 Étiquettes de contrôle doivent être court et concis et suivez les [des conseils de bureau Windows pour les contrôles](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742399\(v=vs.85\).aspx).  
  
 Pour plus d'informations sur le format d'étiquette de contrôle et l'emplacement dans l'interface utilisateur, reportez\-vous à [Présentation de Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md).  
  
#### Liens d'aide  
 Liens d'aide peuvent soit être placés dans le texte d'instructions ou dans le corps de l'interface utilisateur. Vous pouvez être des liens vers l'aide ou lancer des boîtes de dialogue internes.  
  
##### Règles de style visuel pour les liens d'aide  
  
-   Utiliser les couleurs de l'environnement approprié pour les liens hypertexte. Un lien hypertexte appliqué correctement pas brièvement clignote en rouge lorsque vous cliquez sur. Si vous voyez, cela indique que les couleurs de l'environnement ne sont pas utilisés.  
  
-   Soulignements doivent uniquement être utilisées sur pointage ou lorsque le lien est incorporé dans un paragraphe.  
  
-   Pour plus d'informations sur les styles visuels et d'interaction pour les liens hypertexte, consultez boutons et des liens hypertexte.  
  
##### Écrire des règles de style pour les liens d'aide  
  
-   Lors du lancement de boîtes de dialogue, mettre à jour les normes des ellipses : aucune sélection pour la navigation, si la tâche requiert l'interface utilisateur supplémentaire des points de suspension.  
  
     ![Help link in Visual Studio](~/extensibility/ux-guidelines/media/0601-e_helplink.png "0601\-e\_HelpLink")  
  
     **Points de suspension \(...\) dans l'aide un lien indique la tâche requiert l'interface utilisateur supplémentaire.**  
  
-   Liens ne doivent pas commencer par « Apprentissage », car il se n'agit pas d'intention de l'utilisateur. L'utilisateur souhaite répondre à une question spécifique, ne reçoit pas une formation générale.  
  
-   Les liens d'aide d'une expression afin que leur poser la question que la rubrique répondra.  
  
     Incorrect :  
     « En savoir plus sur la tarification Windows Azure Mobile Services »  
  
     Corriger :  
     « Quelles options de tarification sont disponibles pour les Services mobiles Windows Azure? »  
  
-   N'utilisez jamais *cliquez sur...* pour le texte du lien.  
  
-   Jamais le lien uniquement le mot « ici ». Cela pose problème pour certains lecteurs d'écran, qui seront la voix uniquement le lien hypertexte mot.  
  
     Incorrect :  
     « Trouver plus d'informations sur Windows Azure Mobile Services **ici**»  
  
     Corriger :  
     « Quelles options de tarification sont disponibles pour les Services mobiles Windows Azure? »  
  
-   Pour plus d'informations sur le style d'écriture correcte pour les liens d'aide, consultez le [des conseils de bureau Windows de l'aide](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742494\(v=vs.85\).aspx).  
  
#### Texte d'indication  
 Texte d'information apparaît en filigrane dans un contrôle ou sous le contrôle. Mise en forme correcte sera appliquée à l'aide du jeton VSColors approprié, `Environment.GrayText`.  
  
 Il peut apparaître dans plusieurs formes.  
  
-   À la place de l'étiquette de contrôle :  
  
     ![Hint text in Visual Studio](../../extensibility/ux-guidelines/media/0601-f_hinttext1.png "0601\-f\_HintText1")  
  
-   Avec un verbe, ce qui donne des instructions :  
  
     ![Hint text in Visual Studio](../../extensibility/ux-guidelines/media/0601-g_hinttext2.png "0601\-g\_HintText2")  
  
-   Avec le texte qui indique une entrée requise :  
  
     ![Hint text in Visual Studio](../../extensibility/ux-guidelines/media/0601-h_hinttext3.png "0601\-h\_HintText3")  
  
#### Texte de filigrane  
 Sur une aire de conception vide, le texte doit indiquer ce qu'il faut effectuer ainsi que fournir des liens pour ouvrir d'autres fenêtres connexes, le cas échéant :  
  
 ![Watermark text in Visual Studio](../../extensibility/ux-guidelines/media/0601-i_watermarktext.png "0601\-i\_WatermarkText")  
  
 **Exemple de texte de filigrane dans Visual Studio**  
  
### Terminologie courante  
  
|Terme|Explication|Commentaire|  
|-----------|-----------------|-----------------|  
|Connexion \/ déconnexion|Verbes utilisés indifféremment avec le site web pour représenter l'authentification dans une propriété web. Dans les clients, nous utilisons cette fois comme une notion de niveau supérieur pour la signature et la connexion utilisateur IDE, ce qui représente une identité de niveau supérieur qui fournit des fonctionnalités plus haut niveau tels que l'itinérance et Gestionnaire de licences qui ne sont pas disponibles avec toutes les autres connexions.|L'utilisateur de l'IDE est la seule fonctionnalité qui doit représenter une connexion \/ déconnexion verbe, car elle représente le niveau supérieur utilisateur de l'IDE.|  
|Connecter \/ déconnecter|Utiliser dans des lieux où une fonctionnalité maintient une connexion unique à un service en ligne.|Explorateur de serveurs, où vous ne pouvez avoir qu'une seule connexion Azure active à la fois, est un exemple de connexion\/déconnexion.|  
|Ajouter \/ supprimer|Non destructif. À utiliser lors de l'ajout ou la suppression d'éléments dans une liste.|La boîte de dialogue liste de serveur TFS Connection Manager est un exemple d'ajout\/suppression.|  
|Supprimer|Destructeur. Utilisez uniquement lorsque l'élément en cours de suppression est définitivement supprimée ou supprimé du disque.|« Delete » nécessite généralement une invite si le résultat de la suppression d'un fichier à partir du disque.|  
  
## Messages d'erreur  
  
### Vue d'ensemble  
 Des erreurs se produisent. Définition de restrictions sur ce que l'utilisateur peut faire est une première étape dans la prévention des messages d'erreur évitable rationnelle. Toutefois, lorsqu'une erreur se produit, un message d'erreur bien écrite peut aller permettent d'atténuer le problème. Messages d'erreur sont sans doute un des types plus importants de notification que l'utilisateur voit, car elles sont synchrones et indiquent un problème qui doit être résolu. Messages d'erreur mal écrit laissent des utilisateurs sur leurs propres à déterminer la cause des erreurs et des solutions possibles.  
  
 Les utilisateurs peuvent arrêter en faisant attention à l'utilisation excessive ou confusion entre les messages d'erreur, afin de rencontrer des messages d'écriture nécessaire uniquement valeur ajoutée à l'utilisateur. Si le message est simplement une notification, utilisez une autre présentation.  
  
### Règles de création d'un message d'erreur  
  
-   Lors de la construction de messages d'erreur, choisissez le niveau d'erreur approprié pour le public. Point de vue des résumés simples qui fournissent une action de l'utilisateur peut prendre, le cas échéant. État ne pas tout ce que l'utilisateur n'a pas besoin de connaître.  
  
-   Fournir une assistance implicite. Il est plus facile à lire et d'agir sur un message d'erreur qui contient l'instruction.  
  
-   N'utilisez pas deux négatifs.  
  
-   Effectuer les deux un moyen automatisé et manuel grammaire et l'orthographe vérifier tous les messages d'erreur que vous écrivez.  
  
-   Pour les messages d'erreur complexes, évitez de communications séquentielles. N'utilisez jamais une accroche F1 pour le message d'erreur. Le message lui\-même devrait suffire.  
  
-   Utilisez l'icône appropriée.  
  
-   Rendre les questions faciles à comprendre et utiliser les boutons qui ont un choix clair, tels que « Supprimer » et « Annuler ».  
  
-   Pour les avertissements, être clairement ce que sera la conséquence de la procédure. Les boutons doivent indiquer la conséquence.  
  
-   Pour les erreurs, décrivent ce que l'utilisateur peut faire pour résoudre le problème. Boutons à des actions ou dire « Fermer ». N'utilisez pas un bouton « OK » pour un message d'erreur.  
  
-   Certaines questions à se poser lors de la construction d'un message d'erreur :  
  
    -   L'utilisateur peut figure comment résoudre le problème avec cette erreur uniquement ?  
  
    -   L'utilisateur utilise\-t\-il le vocabulaire de même que cette erreur ?  
  
    -   Est cette ambigious erreur ou partagés dans plusieurs situations ? Dans ce cas, comment vous guider les utilisateurs à la solution que dont ils ont besoin ?  
  
#### Erreurs de build  
 Étant donné que Visual Studio est un outil de développement de logiciels, la plupart de ses composants ont une compilation, conversion ou codage étape pour convertir le travail du développeur sous forme binaire. Ces conversions peuvent provoquer des erreurs lorsque le compilateur ne peut pas traiter les fichiers créés de manière incorrecte ou lorsque les options du compilateur n'étaient pas définies correctement.  
  
 Les utilisateurs de Visual Studio peuvent passer une quantité énorme de résolution des erreurs de build d'heures de développement. Ce temps de résolution augmente lorsque les erreurs ont des dépendances ou lorsque les messages d'erreur sont mal écrit, ce qui peut rendre difficile de découvrir la source de l'erreur.  
  
 Des erreurs de build sont ceux qui ne se produisent pas dans le premier emplacement, ce qui explique pourquoi Visual Studio fournit la saisie semi\-automatique et les tildes IntelliSense. Validation de schéma et des outils similaires fournissent le même type de retour. Ces mécanismes proactive guident de l'utilisateur pour construire un code bien formé, ce qui diminue le risque d'erreurs de build.  
  
 Visual Studio fournit une fenêtre outil dans lequel les utilisateurs peuvent lire et parcourir les erreurs qui se sont produites dans les fenêtres de document. Raccourcis clavier sont fournies afin que l'utilisateur peut naviguer rapidement grandes quantités de code et accéder directement à l'emplacement du problème. Visual Studio permet également de chaque erreur de génération d'être rattachés à un ID de mot clé\/contexte d'aide particulier afin que l'utilisateur peut accéder directement à une rubrique d'aide qui fournit des informations plus détaillées sur l'erreur.  
  
 Erreurs de build claire et concise, d'écriture :  
  
-   **Utilisent un langage clair** qui explique le problème avec du jargon de compilateur peu ou pas. Le texte d'erreur de génération ne doit pas être trop technique.  
  
-   **Montrer les causes possibles.** Par exemple, « manque un symbole deux\-points entre la propriété et la valeur dans le ' \(propriété\): \(valeur\)' déclaration. »  
  
-   Fournissez des détails sur les corrections éventuelles. Si l'espace n'est pas suffisant, des détails supplémentaires peuvent être mis dans la rubrique d'aide correspondante.  
  
### Composants d'un message d'erreur bien écrites  
  
#### Utiliser le service de boîte de dialogue de shell pour les messages d'erreur.  
 L'utilisation du service de la boîte de dialogue shell vous permet de contrôler l'apparence du message, en particulier les polices — sans les principales modifications apportées aux éléments individuels. Utilisez le **IErrorInfo** mécanismes et les signaler à l'aide de **IVsUIShell::SetErrorInfo\/ReportErrorInfo**.  
  
#### Choisir une présentation de notification efficace et appropriée.  
 Utilisez une boîte de dialogue modale avec un avertissement critique si une action immédiate est nécessaire pour éviter la perte de données \(notification synchrone\). Icônes critiques sont réservés pour les situations dans le message sans effectuer de lecture de fermeture, cela peut entraîner des conséquences négatives. Une perte de données est une situation critique qui nécessite une réponse au niveau de l'alarme. Utilisation excessive de l'icône critique desensitizes aux utilisateurs de son importance. Si le message d'erreur est de nature informationnelle, prendre en compte les alternatives à une boîte de dialogue modale \(notification asynchrone\).  
  
#### Fournir une explication propre et concise de la cause du problème au lieu d'une explication technique.  
 Surcharger les utilisateurs avec les détails techniques dans l'explication que leur plus probable ignorer les messages d'erreur. Exemples de bon de messagerie :  
  
-   « Impossible d'ouvrir le fichier demandé. »  
  
-   « Impossible de se connecter à Internet. »  
  
#### Fournissent des informations sur la façon de résoudre le problème.  
 Proposer l'utilisateur pour résoudre le problème. Être honnêtes avec l'utilisateur s'il n'y a aucune suggestion. Fournir des liens directs vers les autres sources en ligne, telles que le support technique ou le support de la Communauté. Essayez de dirige les utilisateurs vers des informations en ligne spécifiques se rapportant à ce problème. Pour l'ID d'erreur, envisagez de les lier aux utilisateurs pour une discussion sur cette erreur spécifique. Exemples de bon de messagerie :  
  
-   « Vérifiez que vous êtes connecté à Internet et recommencez l'opération. »  
  
-   « Assurez\-vous que le fichier existe et que vous êtes autorisé à ouvrir. »  
  
#### Écrit un message est court et au point.  
 Un message d'erreur peut notifier, expliquer et offrent une solution mais toujours ignoré s'il est trop longue. Une solution consiste à utiliser progressif avec un bouton de détails. Par exemple, donner une brève description\/solution, puis entrer plus de détails en cliquant sur un bouton Détails. Si les utilisateurs choisissent pour en savoir plus sur l'erreur, ils peuvent le faire.  
  
 La langue du message doit être :  
  
-   **Domaine approprié.** Utiliser le langage que comprenne l'utilisateur. Bien que nos clients sont des développeurs, ils ne disposent pas souvent le contexte et la terminologie que nous avons.  
  
-   **Spécifique.** Évitez les vagues libellé et donner des noms spécifiques et les emplacements des objets impliqués. Par exemple, un message d'erreur tels que « caractère n'est pas valide » n'est pas utile. Le caractère ? « Fichier introuvable ». Le fichier ?  
  
-   **Courtois.** Ne blâmeront pas l'utilisateur ou les rendre sembler stupide. Éviter de langage hostile ou grossier \(arrêter, exécuter, arrêter, irrécupérable, non conforme\). Évitez le texte en majuscules, ce qui est souvent considéré comme trouver et n'est pas lisible par. N'utilisez pas humour.  
  
-   **Corriger.** Utilisez corriger l'orthographe et grammaire \(même en prémultipliés\). Fautes de frappe sont car et ennuyeux.  
  
-   **En fonction du contexte approprié.** Utiliser le texte de bouton approprié. Éviter le bouton « OK » et l'utiliser à la place de « Continue » ou « Yes\/No ».  
  
### Exemples de messages d'erreur  
  
|Bon|Incorrecte|  
|---------|----------------|  
|« Le nombre que vous avez composé n'est plus en service. Veuillez vérifier le numéro et recomposer ou composez le 0 pour l'opérateur ».|-   « Erreur \(449\): nombre non conforme »<br />-   « Cette erreur d'exception non prise en charge indique que l'opération a réussi. »<br /><br /> ![Bad error message in Visual Studio](~/extensibility/ux-guidelines/media/0602-a_errordialog.png "0602\-a\_ErrorDialog")|  
  
## Accéder à l'aide  
  
### Vue d'ensemble  
 Outre la documentation dans MSDN, un utilisateur de Visual Studio possède plusieurs points d'accès afin d'aider l'utilisateur dans l'interface utilisateur. Pour vous assurer que ces points d'accès sont constamment disponibles, les équipes fonctionnelles doivent tirer parti du système d'aide offertes par l'environnement. Ces points d'accès sont :  
  
-   **Texte supplémentaire et les instruction dans les boîtes de dialogue.** Texte statique qui donne une explication, soit sur l'interface utilisateur de surface ou disponible sur passez la souris sur une icône d'info\-bulle ou direction.  
  
-   **F1 Aide** \(éditeur uniquement\). Dans l'éditeur Visual Studio, un utilisateur peut faire confiance qu'à tout moment, en appuyant sur F1 fera apparaître une rubrique d'aide spécifique à la sélection actuelle. Assurez\-vous que les rubriques associées F1 sont appropriées et informatifs.  
  
-   **Liens hypertexte vers des rubriques d'aide.** Un lien hypertexte dans une boîte de dialogue, une fenêtre outil ou une aire de conception qui ouvre une rubrique pour aider l'utilisateur en savoir plus sur une technologie, capacité ou informations sur la façon d'accomplir une tâche.  
  
-   **Mécanismes de l'interface utilisateur d'assistance, tels que les balises actives et les boîtes de dialogue de création.** Ces mécanismes aider l'utilisateur à comprendre un élément d'interface utilisateur, ou facilitent une tâche, telles que des balises actives ou les boîtes de dialogue Générateur de rapports.  
  
-   **L'aide de l'interface utilisateur des boutons** \(déconseillé\). Un indicateur visible dans la barre de titre qui donne accès à la rubrique d'aide F1.  
  
### Texte  
  
#### Texte supplémentaire et les instruction dans les boîtes de dialogue  
 Dans les boîtes de dialogue qui prennent en charge des tâches complexes, il peut être nécessaire pour permettre à texte d'instructions dans l'interface utilisateur, souvent en haut de la boîte de dialogue ou à proximité des contrôles complexes. Consultez [Texte de l'interface utilisateur et la terminologie](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology) Pour plus d'informations sur la règle de style.  
  
#### Info\-bulles  
 Souvent, un texte d'instructions peut être trop long pour positionner en place dans l'interface utilisateur ou peut être utile uniquement aux nouveaux utilisateurs une sensation encombrement aux utilisateurs expérimentés. Dans ce cas, le texte démonstration \/ d'information doit être placé comme une info\-bulle dans une info\-bulle.  
  
 Info\-bulles doivent être placés près les contrôles qu'ils concernent et doivent utiliser l'icône d'info\-bulle spécifique, qui n'est pas discrète notable.  
  
 ![InfoTip in Visual Studio](../../extensibility/ux-guidelines/media/0601-d_infotip.png "0601\-d\_InfoTip")  
  
 **Exemple d'une info\-bulle dans Visual Studio**  
  
### Mécanismes d'aide interactives  
  
#### F1 Aide  
 Aide \(F1\) est requis dans un éditeur ou d'une aire de conception, mais non dans l'environnement Visual Studio.  
  
#### Liens hypertexte vers des rubriques d'aide  
 Liens hypertexte peuvent être utilisés pour effectuer une action, naviguer dans l'IDE ou lancer l'aide dans un navigateur. Consultez [Texte de l'interface utilisateur et la terminologie](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology) Pour plus d'informations sur la langue et 07.10.01 boutons et des liens hypertexte pour connaître les instructions visual et la disposition.  
  
#### Aide des boutons \[?\] dans les barres de titre de boîte de dialogue \(déconseillées\)  
 La plupart du temps, les boutons d'aide \[?\] dans la barre de titre des boîtes de dialogue sont déconseillés. Les rubriques de l'interface utilisateur ne font plus partie de notre modèle de document, et il est donc pas à une rubrique appropriée à lier à. Essentiellement, le bouton de barre de titre est la même chose que la touche F1, et qui n'est plus nécessaire dans les boîtes de dialogue. Dans certains cas, cela peut toujours être utilisé comme un indicateur que plus d'informations conceptuelles ou de procédures est disponible, bien que les liens hypertexte les plus utilisés dans l'interface utilisateur plus récente.  
  
##### Boîtes de dialogue créées par l'environnement.  
 Nombreuses boîtes de dialogue shell sont créés via le **VBDialogBoxParam** \(fonction\). Cette fonction partagée a été mis à jour afin de déplacer le **aide** bouton à partir de la boîte de dialogue le **?** bouton tout en conservant une architecture en amont compatible et extensible.  
  
 Plus précisément, le **VBDialogBoxParam** fonction examine le modèle de boîte de dialogue pour un bouton dont l'ID est **IDHELP** \(9\) ou de l'étiquette est **aide** ou **& aide**. Si un bouton d'aide est trouvé, elle est masquée et la **WS\_EX\_CONTEXTHELP** est ajoutée à la boîte de dialogue, ce qui place la **?** bouton dans la barre de titre de la boîte de dialogue.  
  
 Lorsque la boîte de dialogue est créée, elle exécute un push de la procédure de la boîte de dialogue dans une pile et appelle la boîte de dialogue avec un pré\-traitement proc dialogue nommé **DialogPreProc**. Lors de la **?** bouton est activé, il envoie un **message WM\_SYSCOMMAND** de **SC\_CONTEXTHELP** la boîte de dialogue. Le **DialogPreProc** capture cette commande et le modifie pour un **WM\_HELP** message, qui est passé à la procédure de boîte de dialogue d'origine.  
  
 La plupart des boîtes de dialogue environnement créé ont un bouton Aide dans la boîte de dialogue. Lorsque la boîte de dialogue s'affiche, le bouton aide est masquée automatiquement et que seul le **?** fonctionnement du bouton. Si le **?** bouton jamais supprimé ou modifié dans Windows, cette solution vous permet de ramener rapidement vers les boutons d'origine.  
  
 Cette solution hypothèses quatre pouvant entraîner des bogues :  
  
-   Bouton d'aide de la boîte de dialogue est **IDHELP** \(9\).  
  
-   La boîte de dialogue sont correctes lorsque le bouton est masqué.  
  
-   La boîte de dialogue ne substitue pas son winproc.  
  
-   La boîte de dialogue n'est pas incorporée dans une autre boîte de dialogue.  
  
 Si la boîte de dialogue se trouve dans msenv et n'utilise pas **VBDialogBoxParam**, parti **VBDialogBoxParam** avant d'implémenter votre propre gestionnaire.  
  
##### Boîtes de dialogue créées par le biais d'autres packages  
 Vous pouvez implémenter votre propre solution pour les dialogues qui résident en dehors de msenv. Pour une classe de boîte de dialogue partagée dans votre VSPackage, envisagez de déplacer le bouton à la barre de titre ou l'implémentation d'un gestionnaire dans chaque boîte de dialogue. Le code suivant est une structure d'implémentation pour vous aider à démarrer :  
  
```  
struct DLGPROCITEM { FARPROC proc; // The info used to create the dialog. DLGPROCITEM* procPrev; }; DLGPROCITEM* g_dlgProcStack = NULL; // A dialog starter/wrapper function is used to push the new // dialog proc to the top of our dialog proc stack. int SomeDialogStarterFunction(hinst, id, proc, etc) { if (g_dlgProcStack == NULL) { g_dlgProcStack = new DLGPROCITEM; g_dlgProcStack->procPrev = NULL; } else { DLGPROCITEM* procItem = new DLGPROCITEM; g_dlgProcStack->procPrev = g_dlgProcStack; g_dlgProcStack = procItem; } } // Pop this dialog proc off the dialog proc stack. DialogBoxIndirectParam...(...) { DLGPROCITEM* procItem = g_dlgProcStack->procPrev; delete g_dlgProcStack; g_dlgProcStack = procItem; } // A wrapper dialog procedure will allow us to capture the // SC_CONTEXTHELP button on the title bar from Windows and // forward it as a simple WM_HELP message back to the dialog. INT_PTR CALLBACK DialogPreProc(HWND hwndDlg, UINT uMsg, WPARAM wParam, LPARAM lParam) { if (uMsg == WM_SYSCOMMAND && wParam == SC_CONTEXTHELP) { uMsg = WM_HELP; wParam = 0; lParam = 0; } return CallWindowProc((WNDPROC)g_dlgProcStack->proc, hwndDlg, uMsg, wParam, lParam); }  
```  
  
##### Boutons d'aide dans le code managé  
 Il suffit de substituer le comportement par défaut de la fenêtre titre barre aide du bouton dans le code managé. Voici une application de démonstration complet qui illustre ce comportement. En bref, vous devez remplacer votre formulaire **WndProc** méthode et incendie puis hors tension de l'aide \(F1\) demande quand un **SC\_CONTEXTHELP** message est intercepté.  
  
```  
using System; using System.Windows.Forms; public class HelpForm : Form { private const int SC_CONTEXTHELP = 0xF180; private const int WM_SYSCOMMAND = 0x0112; public HelpForm() { this.ClientSize = new System.Drawing.Size(300, 250); this.HelpButton = true; this.MaximizeBox = false; this.MinimizeBox = false; this.Name = "HelpForm"; this.Text = "Help Form"; } protected override void WndProc(ref Message m) { if (m.Msg == WM_SYSCOMMAND && SC_CONTEXTHELP == (int)m.WParam) ShowHelp(); else base.WndProc(ref m); } private void ShowHelp() { MessageBox.Show("F1 Help goes here."); } [STAThread] static void Main() { Application.EnableVisualStyles(); Application.EnableRTLMirroring(); Application.Run(new HelpForm()); } }  
```  
  
## Voir aussi  
 [Mise en forme pour Visual Studio](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md)   
 [Présentation de Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md)   
 [Notifications et progression pour Visual Studio](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md)