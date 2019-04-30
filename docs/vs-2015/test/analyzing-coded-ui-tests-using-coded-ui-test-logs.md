---
title: Analyse des tests codés de l’interface utilisateur à l’aide des journaux de test codé de l’interface utilisateur | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 7e795873-1d4b-4a13-a52a-a411d87fb759
caps.latest.revision: 15
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 8010ad1f8bbb1e49afe9e5e527e9639f2fb14601
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63442821"
---
# <a name="analyzing-coded-ui-tests-using-coded-ui-test-logs"></a>Analyse des tests codés de l'interface utilisateur à l'aide des journaux de test codé de l'interface utilisateur
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Les journaux de tests codés de l'interface utilisateur filtrent et enregistrent des informations importantes sur l'exécution de vos tests codés de l'interface utilisateur.  
  
 **Spécifications**  
  
- Visual Studio Enterprise  
  
## <a name="why-should-i-do-this"></a>Pourquoi est-ce nécessaire ?  
 Les journaux sont présentés dans un format qui permet de déboguer les problèmes rapidement.  
  
## <a name="how-do-i-do-this"></a>Comment faire ?  
  
### <a name="step-1-enable-logging"></a>Étape 1 : Activer la journalisation  
 Selon votre scénario, appliquez l'une des méthodes suivantes pour activer le journal.  
  
- Cibler .NET Framework version 4 sans fichier App.config présent dans le projet de test  
  
    - Ouvrez le fichier **QTAgent32_40.exe.config**.  
  
         Par défaut, ce fichier se trouve dans **\<lecteur>:\Program Files (x86)\Microsoft Visual Studio 12.0\Common7\IDE**.  
  
         Réglez la valeur de EqtTraceLevel au niveau de journalisation souhaité.  
  
         Enregistrez le fichier.  
  
- Cibler .NET Framework version 4.5 sans fichier App.config présent dans le projet de test  
  
    - Ouvrez le fichier **QTAgent32.exe.config**.  
  
         Par défaut, ce fichier se trouve dans **\<lecteur>:\Program Files (x86)\Microsoft Visual Studio 12.0\Common7\IDE**.  
  
         Réglez la valeur de EqtTraceLevel au niveau de journalisation souhaité.  
  
         Enregistrez le fichier.  
  
- Fichier App.config présent dans le projet de test  
  
    - Ouvrez le fichier App.config dans le projet.  
  
         Ajoutez le code suivant sous le nœud de configuration :  
  
         `<system.diagnostics>     <switches>       <add name="EqtTraceLevel" value="4" />     </switches>  </system.diagnostics>`  
  
- Activer la journalisation à partir du code de test proprement dit  
  
    - <xref:Microsoft.VisualStudio.TestTools.UITesting.PlaybackSettings.LoggerOverrideState%2A> = HtmlLoggerState.AllActionSnapshot;  
  
### <a name="step-2-run-your-coded-ui-test-and-view-the-log"></a>Étape 2 : Exécuter votre test codé de l’interface utilisateur et afficher le journal  
 Quand vous exécutez un test codé de l’interface utilisateur avec les modifications du fichier **QTAgent32.exe.config** en place, vous pouvez constater qu’un lien de sortie figure dans les résultats de l’Explorateur de tests. Des fichiers journaux sont générés non seulement quand votre test échoue, mais aussi quand les tests réussissent si le niveau de trace a la valeur « Commentaires ».  
  
1. Dans le menu **TEST**, choisissez **Fenêtres**, puis **Explorateur de tests**.  
  
2. Dans le menu **BUILD**, choisissez **Générer la solution**.  
  
3. Dans l’Explorateur de tests, sélectionnez le test codé de l’interface utilisateur à exécuter, ouvrez son menu contextuel, puis choisissez **Exécuter les tests sélectionnés**.  
  
     Les tests automatisés s'exécuteront et un message indiquera s'ils ont réussi ou échoué.  
  
    > [!TIP]
    > Pour afficher l’Explorateur de tests depuis le menu **Test**, pointez sur **Windows**, puis choisissez **Explorateur de tests**.  
  
4. Choisissez le lien **Sortie** dans les résultats de l’Explorateur de tests.  
  
     ![Lien de sortie dans l’Explorateur de tests](../test/media/cuit-htmlactionlog1.png "CUIT_HTMLActionLog1")  
  
     Cela permet d'afficher la sortie du test qui inclut un lien vers le journal des actions.  
  
     ![Résultats et liens de sortie du test codé de l’interface utilisateur](../test/media/cuit-htmlactionlog2.png "CUIT_HTMLActionLog2")  
  
5. Choisissez le lien UITestActionLog.html.  
  
     Le journal s'affiche dans votre navigateur web.  
  
     ![Fichier journal du test codé de l’interface utilisateur](../test/media/cuit-htmlactionlog3.png "CUIT_HTMLActionLog3")  
  
## <a name="q--a"></a>Questions et réponses  
  
### <a name="q-what-happened-to-the-enablehtmllogger-key"></a>Q : Qu’est-il arrivé à la clé EnableHtmlLogger ?  
 Dans les versions précédentes de Visual Studio, il existait deux autres paramètres de configuration pour activer l'enregistreur d'événements HTML dans un test codé de l'interface utilisateur :  
  
```  
  
<add key="EnableHtmlLogger" value="true"/>  
  
<add key="EnableSnapshotInfo" value="true"/>  
  
```  
  
 Ces deux paramètres sont dépréciés depuis Visual Studio 2012. EqtTraceLevel est le seul paramètre qui doit être modifié pour activer HtmlLogger.  
  
## <a name="see-also"></a>Voir aussi  
 [Utiliser UI Automation pour tester votre code](../test/use-ui-automation-to-test-your-code.md)   
 [Guide pratique pour exécuter des tests à partir de Microsoft Visual Studio](http://msdn.microsoft.com/library/1a1207a9-2a33-4a1e-a1e3-ddf0181b1046)
