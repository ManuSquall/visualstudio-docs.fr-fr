---
title: "Ex&#233;cuter un test unitaire comme processus 64&#160;bits | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "tests unitaires, créer"
  - "tests unitaires, exécuter"
ms.assetid: d23a9ee7-58e3-4e8b-a38c-b2207ea73fea
caps.latest.revision: 25
ms.author: "mlearned"
manager: "douge"
caps.handback.revision: 25
---
# Ex&#233;cuter un test unitaire comme processus 64&#160;bits
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Si vous avez un ordinateur 64 bits, vous pouvez maintenant exécuter des tests unitaires et capturer les informations de couverture du code en tant que processus 64 bits.  
  
## Exécution d'un test unitaire en tant que processus 64 bits  
  
#### Pour exécuter un test unitaire en tant que processus 64 bits  
  
1.  Si votre code ou vos tests ont été compilés en tant que x86\/32 bits, mais que vous souhaitez maintenant les exécuter en tant que processus 64 bits, vous devez les recompiler en tant qu'**Any CPU** ou éventuellement en tant que **64 bits**.  
  
    > [!TIP]
    >  Pour une flexibilité maximale, vous devez compiler vos projets de test avec la configuration **Any CPU**.  Vous pouvez ensuite les exécuter sur des agents 32 et 64 bits.  La compilation de projets de test avec la configuration **64 bits** ne présente aucun avantage particulier.  
  
2.  Dans le menu de Visual Studio, choisissez **Test**, puis choisissez **Paramètres**, puis choisissez **Architecture de processeur**.  Choisissez **x64** pour exécuter les tests en tant que processus 64 bits.  
  
     \- ou \-  
  
     Spécifiez `<TargetPlatform>x64</TargetPlatform>` dans un fichier de .runsettings.  Un avantage de cette méthode est que vous pouvez spécifier des groupes de paramètres dans des fichiers et de passer rapidement des paramètres.  Vous pouvez également copier des paramètres entre les solutions.  Pour plus d'informations, consultez [Configurer des tests unitaires à l'aide d'un fichier .runsettings](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md).  
  
## Voir aussi  
 [Exécuter des tests unitaires avec l'Explorateur de tests](../test/run-unit-tests-with-test-explorer.md)   
 [Tests unitaires sur votre code](../test/unit-test-your-code.md)   
 [Spécification de paramètres de test pour Visual Studio Tests](/devops-test-docs/test/specifying-test-settings-for-visual-studio-tests)