---
title: "Exécuter un test unitaire comme processus 64 bits | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- unit tests, creating
- unit tests, running
ms.assetid: d23a9ee7-58e3-4e8b-a38c-b2207ea73fea
caps.latest.revision: 25
ms.author: douge
manager: douge
translation.priority.ht:
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
translationtype: Human Translation
ms.sourcegitcommit: 5ab78b6b8eaa8156ed2c8a807b1d8a80e75afa84
ms.openlocfilehash: c5a24ac7491631c87acb66b4ed19a2fc082adab3
ms.lasthandoff: 04/04/2017

---
# <a name="run-a-unit-test-as-a-64-bit-process"></a>Exécuter un test unitaire comme processus 64 bits
Si vous avez un ordinateur 64 bits, vous pouvez exécuter des tests unitaires et capturer les informations de couverture du code en tant que processus 64 bits.  
  
## <a name="running-a-unit-test-as-a-64-bit-process"></a>Exécution d’un test unitaire en tant que processus 64 bits  
  
#### <a name="to-run-a-unit-test-as-a-64-bit-process"></a>Pour exécuter un test unitaire en tant que processus 64 bits  
  
1.  Si votre code ou vos tests ont été compilés en tant que 32-bit/x86, mais que vous souhaitez maintenant les exécuter en tant que processus 64 bits, vous devez les recompiler en tant qu’**Any CPU** ou éventuellement en tant que **64 bits**.  
  
    > [!TIP]
    >  Pour une flexibilité maximale, vous devez compiler vos projets de test avec la configuration **Any CPU**. Vous pouvez ensuite les exécuter sur des agents 32 et 64 bits. La compilation de projets de test avec la configuration **64 bits** ne présente aucun avantage particulier.  
  
2.  Dans le menu de Visual Studio, choisissez **Test**, puis **Paramètres** et enfin **Architecture de processeur**. Choisissez **x64** pour exécuter les tests en tant que processus 64 bits.  
  
     \- ou -  
  
     Spécifiez `<TargetPlatform>x64</TargetPlatform>` dans un fichier .runsettings. Un avantage de cette méthode est que vous pouvez spécifier des groupes de paramètres dans des fichiers différents et changer rapidement de paramètres. Vous pouvez également copier des paramètres entre les solutions. Pour plus d’informations, consultez [Configurer des tests unitaires à l’aide d’un fichier .runsettings](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Exécuter des tests unitaires avec l’Explorateur de tests](../test/run-unit-tests-with-test-explorer.md)   
 [Tests unitaires sur votre code](../test/unit-test-your-code.md)   
 [Spécification des paramètres de test pour les tests Visual Studio](/devops-test-docs/test/specifying-test-settings-for-visual-studio-tests)

