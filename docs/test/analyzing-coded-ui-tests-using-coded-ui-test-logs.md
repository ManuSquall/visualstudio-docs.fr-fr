---
title: Analyse des tests codés de l'interface utilisateur à l'aide des journaux de test codé de l'interface utilisateur
ms.date: 11/04/2016
ms.topic: conceptual
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: ec1025eaa53861fae2cf92395d8842854649fa8c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591214"
---
# <a name="analyzing-coded-ui-tests-using-coded-ui-test-logs"></a>Analyse des tests codés de l’interface utilisateur à l’aide des journaux de test codé de l’interface utilisateur

Les journaux de tests codés de l'interface utilisateur filtrent et enregistrent des informations importantes sur l'exécution de vos tests codés de l'interface utilisateur. Les journaux sont présentés dans un format qui permet de déboguer les problèmes rapidement.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

## <a name="step-1-enable-logging"></a>Étape 1 : Activer la journalisation

Selon votre scénario, appliquez l’une des méthodes suivantes pour activer le journal :

- S’il n’y a aucun fichier *App.config* présent dans votre projet de test :

   1. Déterminez quel processus *QTAgent\*.exe* est lancé lorsque vous exécutez votre test. La seule manière de faire cela est de regarder l’onglet **Détails** dans **Gestionnaire des tâches** Windows.

   2. Ouvrez le fichier *.config* correspondant à partir de la *version\\\<%ProgramFiles(x86)% -Microsoft Visual Studio>\\ \<édition>-Common7-IDE* dossier. Par exemple, si le processus qui s’exécute est *QTAgent_40.exe*, ouvrez *QTAgent_40.exe.config*.

   2. Modifiez la valeur de **EqtTraceLevel** par le niveau de journal souhaité.

      ```xml
      <!-- You must use integral values for "value".
           Use 0 for off, 1 for error, 2 for warn, 3 for info, and 4 for verbose. -->
      <add name="EqtTraceLevel" value="4" />
      ```

   3. Enregistrez le fichier .

- S’il y a un fichier *App.config* présent dans votre projet de test :

  - Ouvrez le fichier *App.config* dans le projet, puis ajoutez le code suivant sous le nœud de configuration :

    ```xml
    <system.diagnostics>
      <switches>
        <add name="EqtTraceLevel" value="4" />
      </switches>
    </system.diagnostics>`
    ```

- Activer la journalisation à partir du code de test proprement dit :

   ```csharp
   Microsoft.VisualStudio.TestTools.UITesting.PlaybackSettings.LoggerOverrideState = HtmlLoggerState.AllActionSnapshot;
   ```

## <a name="step-2-run-your-coded-ui-test-and-view-the-log"></a>Étape 2 : Exécuter votre test codé de l'interface utilisateur et afficher le journal

Quand vous exécutez un test codé de l’interface utilisateur avec les modifications apportées au fichier *QTAgent\*.exe.config* en place, vous constatez qu’un lien de sortie figure dans les résultats de l’**Explorateur de tests**. Des fichiers journaux sont générés non seulement quand votre test échoue, mais aussi quand les tests réussissent si le niveau de trace est défini sur **détaillé**.

1. Dans le menu **Test**, choisissez **Fenêtres**, puis **Explorateur de tests**.

2. Dans le menu **Générer** , choisissez **Générer la solution**.

3. Dans l’**Explorateur de tests**, sélectionnez le test codé de l’interface utilisateur à exécuter, ouvrez son menu contextuel, puis choisissez **Exécuter les tests sélectionnés**.

     Les tests automatisés s’exécutent, puis un message indique s’ils sont une réussite ou un échec.

    > [!TIP]
    > Pour voir **Test Explorer**, choisissez **Test** > **Windows**, puis choisissez Test **Explorer**.

4. Choisissez le lien **Sortie** dans les résultats de l’**Explorateur de tests**.

     ![Lien de sortie dans l'explorateur de tests](../test/media/cuit_htmlactionlog1.png)

     Cela permet d’afficher la sortie du test, qui inclut un lien vers le journal des actions.

     ![Résultats et liens de sortie à partir de test codé de l'interface utilisateur](../test/media/cuit_htmlactionlog2.png)

5. Choisissez le lien *UITestActionLog.html*.

     Le journal s'affiche dans votre navigateur web.

     ![Fichier journal du test codé de l'IU](../test/media/cuit_htmlactionlog3.png)

## <a name="see-also"></a>Voir aussi

- [Utilisez l’automatisation de l’interface utilisateur pour tester votre code](../test/use-ui-automation-to-test-your-code.md)
- [Guide pratique pour exécuter des tests à partir de Microsoft Visual Studio](https://msdn.microsoft.com/Library/1a1207a9-2a33-4a1e-a1e3-ddf0181b1046)
