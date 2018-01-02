---
title: "Rechercher les modifications de code et d’autres historiques avec CodeLens | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 366fdc3483949eb0a83bfad0f51941442430292b
ms.sourcegitcommit: ebe9fb5eda724936f7a059d35d987c29dffdb50d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/07/2017
---
# <a name="find-code-changes-and-other-history-with-codelens"></a>Rechercher les modifications de code et d'autres historiques avec CodeLens

Restez concentré sur votre travail pendant que vous cherchez ce qui est arrivé à votre code, sans quitter l'éditeur. Trouvez les références et les changements relatifs à votre code, les bogues liés, les éléments de travail, les révisions du code et les tests unitaires.

> [!NOTE]
> CodeLens est disponible uniquement dans les éditions Visual Studio Enterprise et Visual Studio Professional. Il n'est pas disponible dans l'édition Visual Studio Community.  

Recherchez où et comment les différentes parties de votre code sont utilisées dans votre solution :  

![Indicateurs CodeLens dans l’éditeur de code](../ide/media/codelensoverview.png "CodeLensOverview")  

Contactez votre équipe à propos de ces modifications dans votre code, sans quitter l'éditeur :  

![CodeLens &#45; Contacter votre équipe](../ide/media/codelensovervew2.png "CodeLensOverview2")  

Pour choisir les indicateurs à visualiser ou pour activer ou désactiver CodeLens, accédez à **Outils**, **Options**, **Éditeur de texte**, **Tous les langages**, **CodeLens**.  

## <a name="FindReferences"></a> Rechercher des références à votre code

Vous aurez besoin de :

-  Visual Studio Enterprise ou Visual Studio Professional

-  Code Visual C# .NET ou Visual Basic .NET

Choisissez l'indicateur de **références** (**Alt+2**). Si vous avez **0 référence**, cela signifie que vous n'avez aucune référence de code Visual C# ou Visual Basic. Ceci n'inclut pas les références d'autres éléments, comme les fichiers XAML et ASPX.

![CodeLens &#45; Choisir l’indicateur des références](../ide/media/codelensviewreferenceslist.png "CodeLensViewReferencesList")  

Pour afficher le code de référencement, placez la souris sur la référence.  

![CodeLens &#45; Aperçu de référence](../ide/media/codelensviewreferencespeekreference.png "CodeLensViewReferencesPeekReference")  

Pour ouvrir le fichier contenant la référence, double-cliquez sur cette dernière.  

Pour afficher les relations entre ce code et ses références, [créez une carte du code](../modeling/map-dependencies-across-your-solutions.md) et choisissez **Afficher toutes les références** dans le menu contextuel de la carte du code.

![CodeLens &#45; Références sur la carte du code](../ide/media/codelensmappedreferences.png "CodeLensMappedReferences")  

## <a name="FindCodeHistory"></a> Rechercher l’historique de votre code et les éléments liés

Examinez l'historique de votre code pour savoir ce qui lui est arrivé. Vous pouvez également examiner les modifications avant qu'elles soient fusionnées dans votre code. Cela vous permet de mieux comprendre la façon dont les modifications des autres branches peuvent affecter votre code.

Vous aurez besoin de :

- Visual Studio Enterprise ou Visual Studio Professional

- Team Foundation Server 2013 ou version ultérieure, Visual Studio Team Services ou Git

- [Lync 2010 ou version ultérieure, ou Skype Entreprise](http://technet.microsoft.com/en-us/lync), pour contacter votre équipe à partir de l’éditeur de code  

Pour le code Visual C# .NET ou Visual Basic .NET stocké avec la gestion de version Team Foundation (TFVC) ou Git, vous obtenez les détails CodeLens au niveau des classes et des méthodes (indicateurs de*niveau élément de code* ). Si votre dépôt Git est hébergé dans TfGit, vous obtenez également des liens vers les éléments de travail TFS.  

![Indicateurs de niveau d’élément dans le code](../ide/media/codelenselementlevelindicators.png "CodeLensElementLevelIndicators")  

Pour tous les autres types de fichiers que vous pouvez ouvrir dans l'éditeur Visual Studio, vous obtenez les détails CodeLens pour l'intégralité du fichier dans un endroit unique au bas de la fenêtre (indicateurs de*niveau fichier* ).

![Indicateurs de niveau d’élément CodeLens](../ide/media/almcodelensfilelevelindicators.png "ALMCodeLensFileLevelIndicators")  

Pour utiliser le clavier afin de sélectionner des indicateurs, maintenez enfoncée la touche **Alt** pour afficher les touches numériques associées.  

![Appuyez sur Alt pour afficher les numéros d’accès clavier](../ide/media/codelensaltkeyindicators.png "CodeLensAltKeyIndicators")  

### <a name="find-changes-in-your-code"></a>Rechercher des modifications dans votre code

Recherchez qui a modifié votre code C# ou Visual Basic, ainsi que les modifications apportées, dans les indicateurs de niveau d'élément de code C’est ce que vous voyez quand vous utilisez la gestion de version Team Foundation (TFVC) dans Team Foundation Server ou Visual Studio Team Services.  

![CodeLens : obtenir l’historique des modifications de votre code dans TFVC](../ide/media/codelenscodechanges.png "CodeLensCodeChanges")  

La période prise en charge par défaut s'étend sur les 12 derniers mois. Si votre code est stocké dans Team Foundation Server, vous pouvez modifier cette période en exécutant la [commande TFSConfig](http://msdn.microsoft.com/en-us/94424190-3b6b-4f33-a6b6-5807f4225b62) avec la [commande CodeIndex](../ide/codeindex-command.md) et l'indicateur **/indexHistoryPeriod** .  

Pour afficher un historique détaillé de toutes les modifications, y compris celles de plus d'un an, choisissez **Afficher toutes les modifications de fichier**.  

![Afficher toutes les modifications du code](../ide/media/codelensshowsallchanges.png "CodeLensShowsAllChanges")  

La fenêtre Historique s'ouvre alors pour les ensembles de modifications.  

![Fenêtre d’historique pour toutes les modifications du code](../ide/media/codelenscodechangeshistory.png "CodeLensCodeChangesHistory")  

Quand vos fichiers sont dans un dépôt Git et que vous choisissez l'indicateur de modifications de niveau d'élément de code, voici ce que vous voyez.  

![CodeLens : obtenir l’historique des modifications de votre code dans Git](../ide/media/codelenscodechangesgit.png "CodeLensCodeChangesGit")  

Recherchez les modifications pour un fichier entier (à l'exception des fichiers C# et Visual Basic) dans les indicateurs de niveau fichier au bas de la fenêtre.  

![CodeLens : obtenir des détails sur le fichier de code](../ide/media/codelensfilelevel.png "CodeLensFileLevel")  

Pour obtenir plus d'informations sur une modification, cliquez avec le bouton droit sur cet élément. Selon que vous utilisez TFVC ou Git, vous obtenez une série d'options permettant de comparer les versions du fichier, d'afficher les détails et d'effectuer le suivi de l'ensemble de modifications, d'obtenir la version sélectionnée du fichier et d'envoyer un courrier électronique à l'auteur de cette modification. Certaines de ces informations apparaissent dans Team Explorer.  

Vous pouvez également voir qui a modifié votre code au fil du temps. Cette fonctionnalité vous permet de découvrir des modèles dans les modifications effectuées par votre équipe, et d’en évaluer l’impact.  

![CodeLens : voir l’historique des modifications du code sous forme de graphique](../ide/media/codelens.png "CodeLens")  

#### <a name="find-changes-in-your-current-branch"></a>Rechercher des modifications dans votre branche actuelle

Supposez que votre équipe a plusieurs branches (une branche principale et un développement enfant) pour réduire le risque de rupture du code stable :  

![CodeLens : rechercher quand une branche a été créée dans votre code](../ide/media/codelensfirstbranchconceptual.png "CodeLensFirstBranchConceptual")  

Découvrez combien de personnes ont modifié votre code et combien de modifications ont été apportées (**Alt + 6**) dans votre branche principale :  

![CodeLens : rechercher le nombre de modifications dans votre branche](../ide/media/codelensbranchchanges.png "CodeLensBranchChanges")  

#### <a name="find-when-your-code-was-branched"></a>Savoir quand une branche a été créée dans votre code

Accédez à votre code dans la branche enfant, par exemple la branche Dev. Choisissez l'indicateur de modifications (**Alt + 6**) :  

![CodeLens : rechercher quand une branche a été créée dans votre code](../ide/media/codelensfirstbranchscreenshot.png "CodeLensFirstBranchScreenshot")  

#### <a name="find-incoming-changes-from-other-branches"></a>Rechercher les modifications entrantes d'autres branches

![CodeLens : rechercher les modifications de code dans d’autres branches](../ide/media/codelensbranchchangecheckinconceptual.png "CodeLensBranchChangeCheckinConceptual")  

...comme cette résolution de bogue dans la branche Dev :

![CodeLens : modification archivée dans une autre branche](../ide/media/codelensbranchchangedevscreenshot.png "CodeLensBranchChangeDevScreenshot")  

Vous pouvez examiner cette modification sans quitter votre branche actuelle (Main) :  

![CodeLens : voir les modifications entrantes d’une autre branche](../ide/media/codelensbranchchangemainscreenshot.png "CodeLensBranchChangeMainScreenshot")  

#### <a name="find-when-changes-got-merged"></a>Savoir quand des modifications ont été fusionnées

Vous pouvez ainsi identifier les modifications qui sont incluses dans votre branche :  

![CodeLens &#45; Modifications fusionnées entre les branches](../ide/media/codelensbranchmergedconceptual.png "CodeLensBranchMergedConceptual")  

Par exemple, votre code dans la branche Main contient maintenant la résolution de bogue de la branche Dev :  

![CodeLens &#45; Modifications fusionnées entre les branches](../ide/media/codelensbranchmergedscreenshot.png "CodeLensBranchMergedScreenshot")  

#### <a name="compare-an-incoming-change-with-your-local-version-shift--f10"></a>Comparer une modification entrante à votre version locale (Maj + F10)

![CodeLens : comparer la modification entrante et la modification locale](../ide/media/codelensbranchincomingchangemenu.png "CodeLensBranchIncomingChangeMenu")  

Vous pouvez également double-cliquer sur l'ensemble de modifications.

#### <a name="what-do-the-icons-mean"></a>Que signifient les icônes ?

|**Icône**|**D’où provient la modification ?**|  
|--------------|-----------------------------------------|  
|![CodeLens : icône Changer à partir de la branche actuelle](../ide/media/codelensbranchcurrenticon.png "CodeLensBranchCurrentIcon")|La branche actuelle|  
|![CodeLens &#45; Icône Changer à partir de la branche parente](../ide/media/codelensbranchparenticon.png "CodeLensBranchParentIcon")|La branche parente|  
|![CodeLens : icône Changer à partir de la branche enfant](../ide/media/codelensbranchchildicon.png "CodeLensBranchChildIcon")|Un branche enfant|  
|![CodeLens &#45; Icône Changer à partir de la branche homologue](../ide/media/codelensbranchpeericon.png "CodeLensBranchPeerIcon")|Une branche homologue|  
|![CodeLens &#45; Icône Changer à partir d’une branche plus éloignée](../ide/media/codelensbranchfurtherawayicon.png "CodeLensBranchFurtherAwayIcon")|Une branche plus éloignée qu'un parent, enfant ou homologue|  
|![CodeLens : icône Fusionner à partir du parent](../ide/media/codelensbranchmergefromparenticon.png "CodeLensBranchMergeFromParentIcon")|Une fusion de la branche parente à une branche enfant|
|![CodeLens : icône Fusionner à partir de la branche enfant](../ide/media/codelensbranchmergefromchildicon.png "CodeLensBranchMergeFromChildIcon")|Une fusion d'une branche enfant à la branche parente|  
|![CodeLens : icône Fusionner à partir d’une branche sans relation](../ide/media/codelensbranchmergefromunrelatedicon.png "CodeLensBranchMergeFromUnrelatedIcon")|Une fusion d'une branche sans relation (fusion sans base)|  

### <a name="find-linked-work-items"></a>Rechercher des éléments de travail liés

![CodeLens &#45; Rechercher des éléments de travail pour un code spécifique](../ide/media/codelensworkitems.png "CodeLensWorkItems")  

### <a name="find-linked-code-reviews"></a>Rechercher des révisions de code liées

![CodeLens &#45; Afficher les demandes de révision du code](../ide/media/codelenscodereviews.png "CodeLensCodeReviews")  

### <a name="find-linked-bugs"></a>Rechercher des bogues liés

![CodeLens &#45; Rechercher les bogues liés aux ensembles de modifications](../ide/media/codelensbugschangesets.png "CodeLensBugsChangesets")  

### <a name="contact-the-owner-of-an-item"></a>Contacter le propriétaire d'un élément

![Contacter le propriétaire d’un élément](../ide/media/codelenscontactitemowner.png "CodeLensContactItemOwner")  

Ouvrez le menu contextuel d'un élément pour afficher les options de contact. Si vous avez installé Lync ou Skype Entreprise, les options suivantes apparaissent :  

![Options de contact pour un élément](../ide/media/codelensitemcontactmenu.png "CodeLensItemContactMenu")  

##  <a name="FindRunUnitTests"></a> Rechercher des tests unitaires pour votre code

Découvrez en plus sur les tests unitaires qui existent pour votre code sans ouvrir l'Explorateur de tests. Vous aurez besoin de :  

-   Visual Studio Enterprise ou Visual Studio Professional  
  
-   Code Visual C# .NET ou Visual Basic .NET  
  
-   Un [projet de test unitaire](../test/unit-test-your-code.md) qui comporte des tests unitaires pour votre code d'application  
  
1.  Accédez au code d'application qui contient des tests unitaires.  
  
2.  Passez en revue les tests pour ce code (**Alt+3**).  
  
     ![CodeLens &#45; Choisir l’état de test dans l’éditeur de code](../ide/media/codelenschoosetestindicator.png "CodeLensChooseTestIndicator")  
  
3.  Si une icône d’avertissement s’affiche ![CodeLens &#45; Avertissement sur les tests unitaires non encore exécutés](../ide/media/codelenstestwarningicon.png "CodeLensTestWarningIcon"), exécutez les tests.  
  
     ![CodeLens &#45; Afficher les tests unitaires non encore exécutés](../ide/media/codelenstestsnotyetrun.png "CodeLensTestsNotYetRun")  
  
4.  Pour passer en revue la définition d'un test, double-cliquez sur l'élément de test dans la fenêtre d'indicateur CodeLens pour ouvrir le fichier de code dans l'éditeur.  
  
     ![CodeLens &#45; Accéder à la définition des tests unitaires](../ide/media/codelensunittestdefinition.png "CodeLensUnitTestDefinition")  
  
5.  Vérifiez les résultats du test. Choisissez l’indicateur d’état de test (![CodeLens &#45; Icône d’échec de test unitaire](../ide/media/codelenstestfailedicon.png "CodeLensTestFailedIcon") ou ![CodeLens &#45; Icône de réussite de test unitaire](../ide/media/codelenstestpassedicon.png "CodeLensTestPassedIcon")), ou appuyez sur **Alt + 1**.  
  
     ![CodeLens &#45; Afficher le résultat de test unitaire](../ide/media/codelensunittestresult.png "CodeLensUnitTestResult")  
  
6.  Pour connaître le nombre de personnes qui ont modifié ce test, savoir qui a modifié ce test ou connaître le nombre de modifications ayant affecté ce test, [Rechercher l'historique de votre code et les éléments liés](#FindCodeHistory).

##  <a name="QA"></a> Q et R

###  <a name="ChangeOrTurnOff"></a> Q : comment activer ou désactiver CodeLens ? Ou comment choisir les indicateurs à afficher ?

**R :**  Vous pouvez activer ou désactiver les indicateurs, à l'exception de l'indicateur des références. Accédez à **Outils**, **Options**, **Éditeur de texte**, **Tous les langages**, **CodeLens**.  
  
 Lorsque les indicateurs sont activés, vous pouvez aussi ouvrir les options CodeLens à partir des indicateurs.  
  
 ![CodeLens &#45; Activer ou désactiver les indicateurs](../ide/media/codelensturnoffonindicatorsfromcode.png "CodeLensTurnOffOnIndicatorsFromCode")  
  
 Activez et désactivez les indicateurs de niveau fichier CodeLens à l'aide des icônes en forme de chevron situées en bas de la fenêtre de l'éditeur.  
  
 ![Activer et désactiver les indicateurs de niveau fichier](../ide/media/codelensfilelevelonandoff.png "CodeLensFileLevelOnAndOff")  
  
###  <a name="NoIndicators"></a>Q : Où est CodeLens ?

**R :** CodeLens apparaît dans le code Visual C# .NET et Visual Basic .NET, au niveau de la méthode, de la classe, de l'indexeur et de la propriété. CodeLens apparaît au niveau du fichier pour tous les autres types de fichiers.

- Assurez-vous que CodeLens est activé. Accédez à **Outils**, **Options**, **Éditeur de texte**, **Tous les langages**, **CodeLens**.  
  
- Si votre code est stocké dans TFS, assurez-vous que l'indexation de code est activée en utilisant la [commande CodeIndex](../ide/codeindex-command.md) avec la [commande TFS Config](http://msdn.microsoft.com/en-us/94424190-3b6b-4f33-a6b6-5807f4225b62).  

- Les indicateurs liés au TFS s'affichent uniquement si des éléments de travail sont liés au code et lorsque vous êtes autorisé à ouvrir les éléments de travail liés. [Confirmez que vous disposez des autorisations de membre de l'équipe.](http://msdn.microsoft.com/en-us/f58805de-ba61-4d09-8f2d-d3ab9662ecfd)  

- Les indicateurs de test unitaire ne s'affichent pas quand le code de l'application ne contient pas de tests unitaires. Les indicateurs d'état de test s'affichent automatiquement dans les projets de test. Si vous savez que le code de votre application contient des tests unitaires, mais que les indicateurs de test ne s'affichent pas, essayez de générer la solution (**Ctrl+Maj+B**).  

### <a name="q-why-dont-i-see-the-work-item-details-for-a-commit"></a>Q : Pourquoi est-ce que je ne vois pas les détails d'élément de travail pour une validation ?

**R :** cela peut se produire si CodeLens ne trouve pas les éléments de travail dans TFS. Vérifiez que vous êtes connecté au projet d'équipe contenant ces éléments de travail et que vous disposez des autorisations nécessaires pour visualiser ces éléments de travail. Cela peut également se produire si la description de validation comporte des informations incorrectes sur les ID d'élément de travail dans TFS.  

###  <a name="NoLync"></a> Q : Pourquoi est-ce que je ne vois pas les indicateurs Lync ou Skype ?

**R :** Ils ne s'affichent pas si vous n'êtes pas connecté à Lync ni à Skype for Business, si vous ne disposez d'aucun de ces logiciels ou si vous ne possédez pas une configuration prise en charge. Toutefois, vous pouvez toujours envoyer du courrier :  

![CodeLens &#45; Contacter le propriétaire de l’ensemble de modifications par courrier](../ide/media/codelenscodesendmailchangesetnolync1.png "CodeLensCodeSendMailChangesetNoLync1")  

 **Quelles sont les configurations de Lync et Skype prises en charge ?**

-   Skype for Business (32 bits ou 64 bits)  

-   Lync 2010 ou version ultérieure individuelle (32 bits ou 64 bits), mais pas Lync Basic 2013 avec Windows 8.1  

CodeLens ne prend pas en charge l'installation de différentes versions de Lync ou de Skype. Elles peuvent ne pas être localisées pour toutes les versions localisées de Visual Studio.  

### <a name="q-how-do-i-change-the-font-and-color-for-codelens"></a>Q : comment changer la police et la couleur de CodeLens ?

**R :** Ouvrez **Outils**, **Options**, **Environnement**, **Polices et couleurs**.  

![CodeLens &#45; Changer les paramètres de police et de couleur](../ide/media/codelensoptionsfontscolorssettings.png "CodeLensOptionsFontsColorsSettings")  

Pour utiliser le clavier :

1.  Appuyez sur **Alt+T+O** pour ouvrir la boîte de dialogue **Options** .  

2.  Appuyez sur **Flèche haut** ou **Flèche bas** pour atteindre le nœud **Environnement** , puis appuyez sur **Flèche gauche** pour développer le nœud.  

3.  Appuyez sur **Flèche bas** pour accéder à **Polices et couleurs**.  

4.  Appuyez sur **Tabulation** pour accéder à la liste **Afficher les paramètres de** , puis appuyez sur **Flèche bas** pour sélectionner **CodeLens**.  

### <a name="q-can-i-move-the-codelens-heads-up-display"></a>Q : Puis-je déplacer l'affichage tête haute CodeLens ?

**R :** Oui, choisissez ![CodeLens &#45; Ancrer en tant que fenêtre](../ide/media/codelensdockwindow.png "CodeLensDockWindow") pour ancrer CodeLens en tant que fenêtre.  

![Ancrer la fenêtre d’indicateur CodeLens](../ide/media/codelensselectdockwindow.png "CodeLensSelectDockWindow")  

![Fenêtre ancrée des références CodeLens](../ide/media/codelensreferencesdockedwindow.png "CodeLensReferencesDockedWindow")  

### <a name="q-how-do-i-refresh-the-indicators"></a>Q : Comment actualiser les indicateurs ?

**R :** cela dépend de l'indicateur :  

-   **Références**: cet indicateur se met automatiquement à jour quand le code change. Si cet indicateur est ancré dans une fenêtre distincte, actualisez-le manuellement ici :  

     ![CodeLens &#45; Ancrer en tant que fenêtre](../ide/media/codelensviewreferencesdocked.png "CodeLensViewReferencesDocked")  

-   **Équipe**: actualisez manuellement ces indicateurs ici :  

     ![CodeLens&#45; Actualiser les indicateurs](../ide/media/codelensrefreshindicatorsfromcode.png "CodeLensRefreshIndicatorsFromCode")  

-   **Test**: [Rechercher des tests unitaires pour votre code](#FindRunUnitTests) pour actualiser cet indicateur.  

###  <a name="LocalVersion"></a> Q : Que signifie « Version locale » ?

**R :** La flèche **Version locale** pointe vers l'ensemble de modifications le plus récent dans votre version locale de ce fichier. Lorsque le serveur possède des ensembles de modifications plus récents, ils apparaissent au-dessus ou en-dessous de la flèche **Version locale** , selon l'ordre utilisé pour trier les ensembles de modifications.  

### <a name="q-can-i-manage-how-codelens-processes-code-to-show-history-and-linked-items"></a>Q : puis-je gérer la façon dont CodeLens traite le code pour afficher l'historique et les éléments liés ?

**R :** oui, si votre code est dans TFS, utilisez la [commande CodeIndex](../ide/codeindex-command.md) avec la [commande TFS Config](http://msdn.microsoft.com/en-us/94424190-3b6b-4f33-a6b6-5807f4225b62).

## <a name="see-also"></a>Voir aussi

[Écrire du code dans l’éditeur de code](../ide/writing-code-in-the-code-and-text-editor.md)