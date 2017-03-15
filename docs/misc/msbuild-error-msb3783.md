---
title: "Erreur MSBuild MSB3783 | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.ResolveSDKReference.MaxPlatformVersionLessThanTargetPlatformVersion"
ms.assetid: 847fc96e-73d3-4aa5-927a-ef8cebc8d3f6
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Erreur MSBuild MSB3783
**MSB3783 : impossible de résoudre le Kit de développement logiciel \(SDK\) « {0} », car il comporte l'attribut MaxPlatformVersion avec la valeur « {1} », qui est inférieure à la valeur de TargetPlatformVersion « {2} ».**  
  
 MSBuild génère cette erreur quand votre projet comporte une dépendance qui n'est pas compatible avec la plateforme ciblée par votre projet.  S'appuyer sur des dépendances incompatibles risque d'entraîner des échecs ou un comportement inattendu des applications au moment de l'exécution.  
  
### Pour corriger cette erreur pour les références du projet  
  
1.  Les projets Visual Basic, C\#, C\+\+ et JavaScript qui ciblent des projets [!INCLUDE[win81](../debugger/includes/win81_md.md)] Store ne peuvent pas faire référence à des projets Windows Store C\+\+ qui ciblent [!INCLUDE[win8](../debugger/includes/win8_md.md)] parce que cela entraîne des problèmes d'exécution.  Si un projet inclus dans votre application cible [!INCLUDE[win81](../debugger/includes/win81_md.md)] et que votre application comprend un projet Windows Store C\+\+, vous devez effectuer les étapes suivantes :  
  
2.  Reciblez tous les projets dans votre application vers [!INCLUDE[win81](../debugger/includes/win81_md.md)].  Pour cela, cliquez avec le bouton droit sur chaque projet dans votre application, en sélectionnant la commande **Recibler vers Windows 8.1** et en cliquant sur **OK** dans la boîte de dialogue **Examen des modifications de projet et de solution**.  
  
3.  Cliquez avec le bouton droit sur chaque projet Visual Basic, C\# et JavaScript qui dépend d'un projet Windows Store C\+\+, choisissez **Ajouter une référence**, accédez à l'onglet **Windows**, puis au sous\-onglet **Extensions**, décochez **Microsoft Visual C\+\+ Runtime Package v11.0** et cochez **Microsoft Visual C\+\+ Runtime Package v12.0**, puis cliquez sur **OK**.  
  
4.  Les projets Windows Store Visual Basic, C\# et JavaScript qui ciblent [!INCLUDE[win81](../debugger/includes/win81_md.md)] peuvent faire référence à des projets Windows Store Visual Basic et C\# qui ciblent [!INCLUDE[win8](../debugger/includes/win8_md.md)], dans la mesure où les projets [!INCLUDE[win8](../debugger/includes/win8_md.md)] Store n'utilisent pas des API déconseillées dans [!INCLUDE[win81](../debugger/includes/win81_md.md)].  Consultez [Migration d’applications Windows 8 vers Windows 8.1](http://msdn.microsoft.com/library/windows/apps/dn263113.aspx) pour vérifier si les projets [!INCLUDE[win8](../debugger/includes/win8_md.md)] Store continueront à se comporter comme prévu quand ils seront référencés à partir d'un projet [!INCLUDE[win81](../debugger/includes/win81_md.md)].  
  
     Les projets [!INCLUDE[win8](../debugger/includes/win8_md.md)] Store ne peuvent pas dépendre de projets Windows Store ou binaires qui ciblent [!INCLUDE[win81](../debugger/includes/win81_md.md)].  
  
### Pour corriger cette erreur pour les références à un Kit de développement logiciel \(SDK\) d'extension  
  
1.  Les projets Windows Store Visual Basic, C\#, C\+\+ et JavaScript qui ciblent [!INCLUDE[win81](../debugger/includes/win81_md.md)] ne peuvent pas faire référence à des Kits de développement logiciel \(SDK\) d'extension qui dépendent de Microsoft Visual C\+\+ Runtime Package v11.0, car cela entraîne des problèmes d'exécution.  Pour déterminer si un Kit de développement logiciel \(SDK\) d'extension dépend de Microsoft Visual C\+\+ Runtime Package v11.0, créez un projet Windows Store C\#, cliquez avec le bouton droit sur le projet et choisissez **Ajouter une référence**. Accédez à l'onglet  **Windows**, puis au sous\-onglet **Extensions**, sélectionnez le Kit de développement logiciel d'extension et vérifiez si le volet droit du **Gestionnaire de références** répertorie **Microsoft.VCLibs, version \= 11.0** en tant que dépendance.  
  
     Les projets Windows Store Visual Basic, C\# et JavaScript qui ciblent [!INCLUDE[win81](../debugger/includes/win81_md.md)] peuvent faire référence à des Kits de développement logiciel \(SDK\) d'extension qui ne dépendent pas de Microsoft Visual C\+\+ Runtime Package v11.0, dans la mesure où ces SDK n'utilisent pas les API déconseillées dans [!INCLUDE[win81](../debugger/includes/win81_md.md)].  Vérifiez auprès du site du fournisseur des SDK d'extension s'ils peuvent être référencés par des projets Store qui ciblent [!INCLUDE[win81](../debugger/includes/win81_md.md)].  
  
     Si vous constatez que le Kit de développement logiciel \(SDK\) d'extension référencé par votre application n'est pas pris en charge, alors vous devez effectuer les étapes suivantes :  
  
2.  Recherchez le nom du projet qui entraîne l'erreur.  La plateforme ciblée par votre projet est indiquée entre parenthèses en regard du nom du projet.  Par exemple, **NomDeMonProjet \(Windows 8.1\)** signifie que votre projet NomDeMonProjet cible la version de plateforme [!INCLUDE[win81](../debugger/includes/win81_md.md)].  
  
3.  Accédez au site du fournisseur qui détient le SDK d'extension non pris en charge et installez la version de celui qui comporte des dépendances compatibles avec la version de la plateforme ciblée par votre projet.  
  
4.  Si le SDK d'extension que vous avez installé précédemment comporte des dépendances vis\-à\-vis d'autres SDK d'extension, accédez au\(x\) site\(s\) du ou des fournisseurs qui possèdent les dépendances et installez les versions de ces dépendances qui sont compatibles avec la version de la plateforme ciblée par votre projet.  
  
    > [!NOTE]
    >  Si votre projet cible [!INCLUDE[win81](../debugger/includes/win81_md.md)] et que le SDK d'extension installé précédemment comporte une dépendance vis\-à\-vis de Microsoft Visual C\+\+ Runtime Package, la version de Microsoft Visual C\+\+ Runtime Package qui est compatible avec Windows 8.1 est v12.0 et est installée avec [!INCLUDE[vs_dev12](../data-tools/includes/vs_dev12_md.md)].  
  
    > [!NOTE]
    >  Pour savoir si le SDK d'extension installé précédemment comporte des dépendances vis\-à\-vis d'autres SDK d'extension, redémarrez Visual Studio, créez un projet Windows Store C\#, cliquez avec le bouton droit sur le projet et choisissez **Ajouter une référence**, accédez à l'onglet **Windows**, accédez au sous\-onglet **Extensions**, sélectionnez le SDK d'extension et examinez le volet droit du **Gestionnaire de références**.  S'il possède des dépendances, elles y sont répertoriées.  
  
5.  Redémarrez Visual Studio et ouvrez votre application.  
  
6.  Cliquez avec le bouton droit sur le projet à l'origine de l'erreur et choisissez **Ajouter une référence** en cas de projets Visual Basic, C\# ou JavaScript, ou sur **Références** en cas de projets C\+\+.  Pour les projets C\+\+, cliquez ensuite sur le bouton Ajouter une nouvelle référence.  
  
7.  Cliquez sur l'onglet **Windows**, puis le sous\-onglet **Extensions**.  Décochez les cases en regard des anciens SDK d'extension et cochez les cases en regard des nouveaux SDK d'extension.  Cliquez sur **OK**.