---
title: "MSBuild Error MSB3190 | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "GenerateManifest.InvalidRequestedExecutionLevel"
helpviewer_keywords: 
  - "MSB3190"
ms.assetid: 45b45688-9345-45db-adc8-3e200f1c17eb
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild Error MSB3190
**MSB3190: ClickOnce ne prend pas en charge le niveau d'exécution demandé '\<niveau\>'.**  
  
 Cette erreur est générée sur les ordinateurs qui exécutent Windows Vista lorsque le manifeste de contrôle de compte d'utilisateur \(UAC, User Account Control\) incorporé de l'application spécifie qu'une application ClickOnce s'exécute avec les informations d'identification d'administratives.  ClickOnce et COM sans inscription requièrent un manifeste externe qui spécifie que l'application s'exécute en tant qu'utilisateur actuel.  
  
 ClickOnce n'accepte pas les niveaux d'exécution`requireAdministrator` ou `highestAvailable`.  Si vous spécifiez l'un de ces niveaux, vous recevrez ce message d'erreur.  ClickOnce requiert `asInvoker`, mais n'acceptera par ailleurs aucun nœud `<requestedExecutionLevel>` qui spécifie la virtualisation des fichiers\/registres \(c'est\-à\-dire qu'aucun manifeste n'est généré pour des raisons de compatibilité descendante\).  
  
> [!NOTE]
>  Il est possible que pour certains des éléments de l'interface utilisateur de Visual Studio, votre ordinateur affiche des noms ou des emplacements différents de ceux indiqués dans les instructions suivantes.  Ces éléments dépendent de l'édition de Visual Studio dont vous disposez et des paramètres que vous utilisez.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### Pour corriger cette erreur  
  
-   Générez un manifeste de contrôle de compte d'utilisateur externe \(app.manifest\) qui spécifie que l'application s'exécute en tant qu'utilisateur actuel \(`asInvoker`\).  
  
     Dans les projets Visual C\#, allez à la page **Application** du Concepteur de projets et cliquez sur **Propriétés\\app.manifest** dans la liste **Manifeste**.  Pour plus d'informations, consultez [Page Application, Concepteur de projets \(C\#\)](../ide/reference/application-page-project-designer-csharp.md).  
  
     Dans les projets Visual Basic, allez à la page **Application** du Concepteur de projets et cliquez sur le bouton **Afficher les paramètres UAC**.  Cette procédure ouvre app.manifest pour vous permettre de le modifier.  Modifiez la balise suivante dans le manifeste pour qu'elle se présente comme suit :  
  
    ```  
    <requestedExecutionLevel level="asInvoker" />  
    ```  
  
     Pour plus d'informations, consultez [Page Application, Concepteur de projets \(Visual Basic\)](../ide/reference/application-page-project-designer-visual-basic.md).  
  
-   Pour plus d'informations sur la génération d'un manifeste de contrôle de compte d'utilisateur et sur la spécification du niveau d'exécution, consultez [ClickOnce Deployment on Windows Vista](../deployment/clickonce-deployment-on-windows-vista.md).  
  
## Voir aussi  
 [Page Application, Concepteur de projets \(C\#\)](../ide/reference/application-page-project-designer-csharp.md)   
 [Page Application, Concepteur de projets \(Visual Basic\)](../ide/reference/application-page-project-designer-visual-basic.md)   
 [ClickOnce Deployment on Windows Vista](../deployment/clickonce-deployment-on-windows-vista.md)