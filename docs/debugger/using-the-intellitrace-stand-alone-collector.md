---
title: Utilisation du collecteur autonome IntelliTrace | Microsoft Docs
description: Utilisez le collecteur autonome IntelliTrace pour collecter des données sans installer Visual Studio et sans modifier l’environnement du système cible.
ms.custom: SEO-VS-2020
ms.date: 07/30/2019
ms.topic: conceptual
f1_keywords:
- vs.historicaldebug.collectdataoutsideVS
helpviewer_keywords:
- IntelliTrace, debugging applications in production
ms.assetid: 1bde9807-8219-4a2a-a440-ac5ee5178159
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cbdd7e948aaafff8e90aa8e67907c9a53471b05c
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/13/2021
ms.locfileid: "98150078"
---
# <a name="using-the-intellitrace-stand-alone-collector-c-visual-basic"></a>Utilisation du collecteur autonome IntelliTrace (C#, Visual Basic)

Le **collecteur autonome IntelliTrace** vous permet de collecter des données de diagnostic IntelliTrace pour vos applications exécutées sur des serveurs de production ou d’autres environnements, sans avoir à installer Visual Studio sur l’ordinateur cible ni à modifier l’environnement du système cible. Ce collecteur fonctionne avec les applications web, SharePoint, WPF et Windows Forms. Quand vous avez terminé la collecte des données, supprimez simplement le collecteur pour le désinstaller.

 Regardez IntelliTrace en action : [Collecte et analyse des données IntelliTrace dans l’environnement de production pour le débogage (vidéo Channel 9)](https://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Collecting-and-analyzing-data-in-production)

> [!NOTE]
> Vous pouvez également collecter les mêmes données IntelliTrace pour les applications web et SharePoint s’exécutant sur des ordinateurs distants à l’aide de **Microsoft Monitoring Agent** en mode **Trace** .
>
> Vous pouvez collecter les événements de performances dans les données IntelliTrace en exécutant l’agent en mode **Monitor** . Le mode **Monitor** a moins d’impact sur les performances que le mode **Trace** ou le **collecteur autonome IntelliTrace**. Microsoft Monitoring Agent modifie l’environnement du système cible quand il est installé. Consultez [utilisation de l’Microsoft Monitoring agent](../debugger/using-the-microsoft-monitoring-agent.md).
> Le collecteur autonome IntelliTrace ne prend pas en charge les instantanés de processus.

 **Configuration requise**

- .NET Framework 3,5 ou version ultérieure

- Visual Studio Enterprise (mais pas les éditions Professional ou Community) sur un ordinateur de développement ou autre pour ouvrir les fichiers .iTrace

  > [!NOTE]
  > Assurez-vous d’enregistrer vos fichiers de symboles (.pdb). Pour déboguer avec IntelliTrace et exécuter le code pas à pas, vous devez disposer des fichiers sources et des fichiers de symboles correspondants. Consultez [diagnostiquer des problèmes après le déploiement](../debugger/diagnose-problems-after-deployment.md).

  **FORUM AUX QUESTIONS**

- [Quelles applications fonctionnent avec le collecteur ?](#WhatApps)

- [Comment faire pour démarrer ?](#GetStarted)

- [Comment puis-je obtenir le maximum de données sans ralentir mon application ?](#Minimizing)

- [À quel autre endroit puis-je trouver des données IntelliTrace ?](#WhereElse)

## <a name="what-apps-work-with-the-collector"></a><a name="WhatApps"></a> Quelles applications fonctionnent avec le collecteur ?

- Applications Web ASP.NET hébergées sur Internet Information Services (IIS) version 7,0, 7,5, 8,0, 12,0 et 16,0

- Applications SharePoint 2010 et SharePoint 2013

- Applications Windows Presentation Foundation (WPF) et Windows Forms.

## <a name="how-do-i-get-started"></a><a name="GetStarted"></a> Comment faire commencer ?

1. [Installer le collecteur](#BKMK_Install_the_IntelliTrace_Stand_Alone_Collector)

2. [Définir les autorisations pour le répertoire du collecteur](#ConfigurePermissionsRunningCollector)

3. [Installer les applets de commande PowerShell IntelliTrace pour collecter les données pour les applications web ou les applications SharePoint](#BKMK_Set_up_the_IntelliTrace_PowerShell_commandlets)

4. [Définir les autorisations du répertoire de fichiers .iTrace](#BKMK_Create_and_Configure_a_Log_File_Directory)

5. [Collecter les données d’une application web ou d’une application SharePoint](#BKMK_Collect_Data_from_IIS_Application_Pools)

     -ou-

     [Collecter les données d’une application managée](#BKMK_Collect_Data_from_Executables)

6. [Ouvrez le fichier .iTrace dans Visual Studio Enterprise](#BKMK_View_IntelliTrace_Log_Files)

## <a name="install-the-collector"></a><a name="BKMK_Install_the_IntelliTrace_Stand_Alone_Collector"></a> Installer le collecteur

1. Sur le serveur de votre application, créez le répertoire du collecteur, par exemple : **C:\IntelliTraceCollector**

2. Récupérez le collecteur à partir du [Centre de téléchargement Microsoft](https://visualstudio.microsoft.com/downloads/#intellitrace-standalone-collector-for-visual-studio-2019), [My.VisualStudio.com](https://my.visualstudio.com/Downloads?q=intellitrace%20standalone%20collector%20visual%20studio%202017), ou à partir du dossier d’installation Visual Studio 2013 Update 3. [Collecteur IntelliTrace pour Visual Studio 2013 Update 4](https://www.microsoft.com/download/details.aspx?id=44909):

   - **Centre de téléchargement Microsoft** ou **My.VisualStudio.com**:

     1. À côté de **IntelliTraceCollector.exe**, choisissez **Télécharger**.

     2. Enregistrez IntelliTraceCollector.exe dans le répertoire du collecteur, par exemple **C:\IntelliTraceCollector**

     3. Exécutez IntelliTraceCollector.exe. Cette opération extrait le fichier IntelliTraceCollection.cab.

        \- ou -

   - **Dossier d’installation de Visual Studio**:

     1. Copiez IntelliTraceCollection.cab à partir du dossier où le collecteur est installé, par exemple :

          **.. \Microsoft Visual Studio\2019\Enterprise\Common7\IDE\CommonExtensions\Microsoft\IntelliTrace**

          ou, pour les versions antérieures de Visual Studio :

          **..\Microsoft Visual Studio 12.0\Common7\IDE\CommonExtensions\Microsoft\IntelliTrace\12.0.0**

     2. Placez IntelliTraceCollection.cab dans le répertoire du collecteur, par exemple **C:\IntelliTraceCollector**

3. Développez IntelliTraceCollection.cab :

   1. Sur le serveur de votre application, ouvrez une fenêtre d’invite de commandes en tant qu’administrateur.

   2. Accédez au répertoire du collecteur, par exemple **C:\IntelliTraceCollector**

   3. Exécutez la commande **expand** suivante, avec le point (**.**) à la fin, pour développer IntelliTraceCollection.cab :

        `expand  /f:* IntelliTraceCollection.cab .`

       > [!NOTE]
       > Le point (**.**) permet de conserver les sous-dossiers qui contiennent les plans de collecte localisés.

## <a name="set-up-permissions-for-the-collector-directory"></a><a name="ConfigurePermissionsRunningCollector"></a> Définir des autorisations pour le répertoire du collecteur

1. Sur le serveur de votre application, ouvrez une fenêtre d’invite de commandes en tant qu’administrateur.

2. Utilisez la commande Windows **icacls** pour accorder à l’administrateur du serveur toutes les autorisations d’accès au répertoire du collecteur. Exemple :

     `icacls "C:\IntelliTraceCollector" /grant "` *\<Domain\AdministratorID>* `":F`

3. Pour collecter les données d’une application web ou SharePoint :

    1. Accordez à l’utilisateur qui exécutera les applets de commande PowerShell IntelliTrace toutes les autorisations d’accès au répertoire du collecteur.

         Exemple :

         `icacls "C:\IntelliTraceCollector" /grant "` *\<Domain\UserID>* `":F`

    2. Accordez au pool d’applications hébergeant l’application web ou SharePoint les autorisations de lecture et d’exécution pour le répertoire du collecteur.

         Exemple :

        - Pour une application web du pool d’applications **DefaultAppPool** :

             `icacls "C:\IntelliTraceCollector" /grant "IIS APPPOOL\DefaultAppPool":RX`

        - Pour une application SharePoint du pool d’applications **SharePoint – 80** :

             `icacls "C:\IntelliTraceCollector" /grant "IIS APPPOOL\SharePoint - 80":RX`

## <a name="install-intellitrace-powershell-cmdlets-to-collect-data-for-web-apps-or-sharepoint-applications"></a><a name="BKMK_Set_up_the_IntelliTrace_PowerShell_commandlets"></a> Installer des applets de commande PowerShell IntelliTrace pour collecter des données pour les applications Web ou les applications SharePoint

1. Sur le serveur de votre application, vérifiez que PowerShell est activé. Dans la plupart des versions de Windows Server, vous pouvez ajouter cette fonctionnalité dans l’outil d’administration **Gestionnaire de serveur** .

     ![Ajout de PowerShell à l’aide du Gestionnaire de serveur](../debugger/media/intellitrace_servermanager_addpowershell.png "INTELLITRACE_ServerManager_AddPowerShell")

2. Installez les applets de commande PowerShell IntelliTrace.

    1. Ouvrez une fenêtre de commande PowerShell en tant qu’administrateur.

        1. Choisissez **Démarrer**, **Tous les programmes**, **Accessoires**, **Windows PowerShell**.

        2. Choisissez l’une des étapes suivantes :

            - Sur les systèmes d’exploitation 64 bits, ouvrez le menu contextuel de **Windows PowerShell**. Sélectionnez **Exécuter en tant qu’administrateur**.

            - Sur les systèmes d’exploitation 32 bits, ouvrez le menu contextuel de **Windows PowerShell (x86)**. Sélectionnez **Exécuter en tant qu’administrateur**.

    2. Dans la fenêtre Commande PowerShell, utilisez la commande **Import-Module** pour importer **Microsoft.VisualStudio.IntelliTrace.PowerShell.dll**.

         Exemple :

         `Import-Module "C:\IntelliTraceCollector\Microsoft.VisualStudio.IntelliTrace.PowerShell.dll"`

## <a name="set-up-permissions-for-the-itrace-file-directory"></a><a name="BKMK_Create_and_Configure_a_Log_File_Directory"></a> Définir des autorisations pour le répertoire de fichiers. iTrace

1. Sur le serveur de votre application, créez le répertoire de fichiers .iTrace, par exemple : **C:\IntelliTraceLogFiles**

   > [!NOTE]
   > - Pour éviter de ralentir votre application, choisissez un emplacement sur un disque local rapide et qui n’est pas très actif.
   >   - Vous pouvez placer les fichiers .iTrace et ceux du collecteur dans le même emplacement. Dans le cas d’une application web ou SharePoint, cet emplacement doit se trouver en dehors du répertoire qui héberge cette application.
   >
   > [!IMPORTANT]
   > - Limitez l’accès au répertoire de fichiers .iTrace uniquement aux identités qui ont besoin d’utiliser le collecteur. Un fichier .iTrace peut contenir des informations sensibles, telles que les données provenant d’utilisateurs, de bases de données ou d’autres emplacements sources, ainsi que des chaînes de connexion. En effet, IntelliTrace est susceptible d’enregistrer toutes les données passées dans les paramètres de méthode ou en tant que valeurs de retour.
   >   - Assurez-vous que les utilisateurs qui peuvent ouvrir les fichiers .iTrace ont l’autorité pour afficher des données sensibles. Partagez les fichiers .iTrace avec précaution. Si d’autres utilisateurs doivent accéder aux fichiers, copiez ces fichiers dans un emplacement partagé sécurisé.

2. Pour une application web ou SharePoint, accordez au pool d’applications correspondant toutes les autorisations d’accès au répertoire de fichiers .iTrace. Pour cela, utilisez au choix la commande Windows **icacls** ou l’Explorateur Windows (ou l’Explorateur de fichiers).

    Exemple :

   - Pour définir des autorisations avec la commande Windows **icacls** :

     - Pour une application web du pool d’applications **DefaultAppPool** :

        `icacls "C:\IntelliTraceLogFiles" /grant "IIS APPPOOL\DefaultAppPool":F`

     - Pour une application SharePoint du pool d’applications **SharePoint – 80** :

        `icacls "C:\IntelliTraceLogFiles" /grant "IIS APPPOOL\SharePoint - 80":F`

       -ou-

   - Pour définir des autorisations avec l’Explorateur Windows (ou l’Explorateur de fichiers) :

     1. Ouvrez **Propriétés** pour le répertoire de fichiers .iTrace.

     2. Sous l’onglet **Sécurité** , choisissez **Modifier**, puis **Ajouter**.

     3. Vérifiez que l’élément **Principaux de sécurité intégrés** est affiché dans la zone **Sélectionnez le type de cet objet** . S’il n’y est pas, choisissez **Types d’objets** pour l’ajouter.

     4. Vérifiez que votre ordinateur local apparaît dans la zone **À partir de cet emplacement** . S’il n’est pas présent, choisissez **Emplacements** pour le modifier.

     5. Dans la zone **Entrez les noms des objets à sélectionner** , ajoutez le pool d’applications de l’application web ou SharePoint.

     6. Choisissez **Vérifier les noms** pour résoudre le nom. Choisissez **OK**.

     7. Vérifiez que le pool d’applications dispose des autorisations **Contrôle total**.

## <a name="collect-data-from-a-web-app-or-sharepoint-application"></a><a name="BKMK_Collect_Data_from_IIS_Application_Pools"></a> Collecter des données à partir d’une application Web ou d’une application SharePoint

1. Pour démarrer la collecte des données, ouvrez une fenêtre Commande PowerShell en tant qu’administrateur, puis exécutez la commande suivante :

     `Start-IntelliTraceCollection` `"` *\<ApplicationPool>* `"` *\<PathToCollectionPlan>* *\<FullPathToITraceFileDirectory>*

    > [!IMPORTANT]
    > Après avoir exécuté cette commande, tapez **Y** pour confirmer que vous souhaitez démarrer la collecte des données.

     Par exemple, pour collecter des données d’une application SharePoint exécutée dans le pool d’applications **SharePoint - 80** , exécutez :

     `Start-IntelliTraceCollection "SharePoint - 80" "C:\IntelliTraceCollector\collection_plan.ASP.NET.default.xml" "C:\IntelliTraceLogFiles"`

    |Nom|Description|
    |-|-|
    |*ApplicationPool*|Nom du pool d’applications dans lequel votre application s’exécute.|
    |*PathToCollectionPlan*|Chemin d’accès à un plan de collecte, un fichier .xml qui configure les paramètres du collecteur.<br /><br /> Vous pouvez spécifier un plan qui est fourni avec le collecteur. Les plans suivants fonctionnent avec les applications web et SharePoint :<br /><br /> -   collection_plan.ASP.NET.default.xml<br />     Collecte uniquement les événements IntelliTrace et les événements SharePoint, y compris les exceptions, les appels de base de données et les demandes de serveur web.<br />-   collection_plan.ASP.NET.trace.xml<br />     Collecte les appels de fonction et toutes les données du plan collection_plan.ASP.NET.default.xml. Ce plan est approprié pour une analyse détaillée, mais il risque de ralentir votre application davantage que le plan collection_plan.ASP.NET.default.xml.<br /><br /> Pour éviter de ralentir votre application, personnalisez ces plans ou créez votre propre plan. Pour des raisons de sécurité, placez tous les plans personnalisés dans le même emplacement sécurisé que les fichiers du collecteur. Consultez [Créer et personnaliser des plans de collecte IntelliTrace](https://devblogs.microsoft.com/devops/modifying-an-intellitrace-collection-plan-for-the-stand-alone-collector/) et [Comment puis-je obtenir le maximum de données sans ralentir mon application ?](#Minimizing) **Remarque :**  Par défaut, la taille maximale du fichier. iTrace est de 100 Mo. Quand le fichier .iTrace atteint cette limite, le collecteur supprime les entrées les plus anciennes du fichier pour faire de la place aux nouvelles entrées. Pour changer cette limite, modifiez l’attribut `MaximumLogFileSize` du plan de collecte. <br /><br /> *Où puis-je trouver des versions localisées de ces plans de collecte ?*<br /><br /> Les plans de collecte localisés sont situés dans les sous-dossiers du collecteur.|
    |*FullPathToITraceFileDirectory*|Chemin d’accès complet au répertoire de fichiers .iTrace. **Remarque relative à la sécurité :**  Indiquez le chemin d’accès complet, et non un chemin d’accès relatif.|

     Le collecteur se connecte au pool d’applications et commence la collecte de données.

     *Puis-je ouvrir le fichier .iTrace en même temps ?* Non. Le fichier est verrouillé pendant la collecte des données.

2. Reproduisez le problème.

3. Pour créer un point de contrôle du fichier. iTrace, utilisez la syntaxe suivante :

     `Checkpoint-IntelliTraceCollection` `"` *\<ApplicationPool>* `"`

4. Pour vérifier l’état de la collecte, utilisez la syntaxe suivante :

     `Get-IntelliTraceCollectionStatus`

5. Pour arrêter la collecte de données, utilisez la syntaxe suivante :

     `Stop-IntelliTraceCollection` `"` *\<ApplicationPool>* `"`

    > [!IMPORTANT]
    > Après avoir exécuté cette commande, tapez **Y** pour confirmer que vous souhaitez arrêter la collecte de données. Sinon, le collecteur risque de continuer la collecte des données, le fichier iTrace restera verrouillé ou le fichier ne contiendra peut-être aucunes données utiles.

6. [Ouvrez le fichier .iTrace dans Visual Studio Enterprise](#BKMK_View_IntelliTrace_Log_Files)

## <a name="collect-data-from-a-managed-app"></a><a name="BKMK_Collect_Data_from_Executables"></a> Collecter des données à partir d’une application gérée

1. Pour démarrer votre application et collecter des données en même temps, utilisez la syntaxe suivante :

     *\<FullPathToIntelliTraceCollectorExecutable>* `\IntelliTraceSC.exe launch /cp:` *\<PathToCollectionPlan>* `/f:` *\<FullPathToITraceFileDirectoryAndFileName>* *\<PathToAppExecutableFileAndFileName>*

     Par exemple, pour collecter des données d’une application nommée **MyApp**, exécutez :

     `C:IntelliTraceCollectorIntelliTraceSC.exe launch /cp:"C:IntelliTraceCollectorcollection_plan.ASP.NET.default.xml" /f:"C:IntelliTraceLogFilesMyApp.itrace" "C:MyAppMyApp.exe"`

    |Nom|Description|
    |-|-|
    |*FullPathToIntelliTraceCollectorExecutable*|Chemin d’accès complet à l’exécutable du collecteur (IntelliTraceSC.exe).|
    |*PathToCollectionPlan*|Chemin d’accès à un plan de collecte, un fichier .xml qui configure les paramètres du collecteur.<br /><br /> Vous pouvez spécifier un plan qui est fourni avec le collecteur. Les plans suivants fonctionnent avec les applications managées :<br /><br /> -   collection_plan.ASP.NET.default.xml<br />     Collecte uniquement les événements IntelliTrace, y compris les exceptions, les appels de base de données et les demandes de serveur web.<br />-   collection_plan.ASP.NET.trace.xml<br />     Collecte les appels de fonction et toutes les données du plan collection_plan.ASP.NET.default.xml. Ce plan est approprié pour une analyse détaillée, mais il risque de ralentir votre application davantage que le plan collection_plan.ASP.NET.default.xml.<br /><br /> Pour éviter de ralentir votre application, personnalisez ces plans ou créez votre propre plan. Pour des raisons de sécurité, placez tous les plans personnalisés dans le même emplacement sécurisé que les fichiers du collecteur. Consultez [Créer et personnaliser des plans de collecte IntelliTrace](https://devblogs.microsoft.com/devops/modifying-an-intellitrace-collection-plan-for-the-stand-alone-collector/) et [Comment puis-je obtenir le maximum de données sans ralentir mon application ?](#Minimizing) **Remarque :**  Par défaut, la taille maximale du fichier. iTrace est de 100 Mo. Quand le fichier .iTrace atteint cette limite, le collecteur supprime les entrées les plus anciennes du fichier pour faire de la place aux nouvelles entrées. Pour changer cette limite, modifiez l’attribut `MaximumLogFileSize` du plan de collecte. <br /><br /> *Où puis-je trouver des versions localisées de ces plans de collecte ?*<br /><br /> Les plans de collecte localisés sont situés dans les sous-dossiers du collecteur.|
    |*FullPathToITraceFileDirectoryAndFileName*|Chemin d’accès complet au répertoire du fichier .iTrace et nom du fichier .iTrace avec l’extension **.itrace** . **Remarque relative à la sécurité :**  Indiquez le chemin d’accès complet, et non un chemin d’accès relatif.|
    |*PathToAppExecutableFileAndFileName*|Chemin d’accès et nom de fichier de votre application managée.|

2. Arrêtez la collecte de données en quittant l’application.

3. [Ouvrez le fichier .iTrace dans Visual Studio Enterprise](#BKMK_View_IntelliTrace_Log_Files)

## <a name="open-the-itrace-file-in-visual-studio-enterprise"></a><a name="BKMK_View_IntelliTrace_Log_Files"></a> Ouvrez le fichier. iTrace dans Visual Studio Enterprise

> [!NOTE]
> Pour déboguer avec IntelliTrace et exécuter le code pas à pas, vous devez disposer des fichiers sources et des fichiers de symboles correspondants. Consultez [diagnostiquer des problèmes après le déploiement](../debugger/diagnose-problems-after-deployment.md).

1. Déplacez le fichier .iTrace ou copiez-le sur un ordinateur équipé de Visual Studio Enterprise (mais pas les éditions Professional ou Community).

2. Double-cliquez sur le fichier .iTrace en dehors de Visual Studio ou ouvrez le fichier à partir de Visual Studio.

     Visual Studio affiche la page **Résumé IntelliTrace** . Dans la plupart des sections, vous pouvez passer en revue les événements ou autres éléments enregistrés, choisir un élément, puis commencer le débogage avec IntelliTrace à partir de l’endroit et du moment où l’événement s’est produit. Consultez [utilisation des données IntelliTrace enregistrées](../debugger/using-saved-intellitrace-data.md).

    > [!NOTE]
    > Pour déboguer avec IntelliTrace et exécuter le code pas à pas, vous devez disposer des fichiers sources et des fichiers de symboles correspondants sur votre ordinateur de développement. Consultez [diagnostiquer des problèmes après le déploiement](../debugger/diagnose-problems-after-deployment.md).

## <a name="how-do-i-get-the-most-data-without-slowing-down-my-app"></a><a name="Minimizing"></a> Comment faire obtient-il le maximum de données sans ralentir mon application ?
 IntelliTrace peut collecter beaucoup de données. L’impact de la collecte sur les performances de votre application dépend donc de la quantité de données collectées et du type de code analysé par IntelliTrace. Consultez [Optimisation de la collecte IntelliTrace sur les serveurs de production](https://devblogs.microsoft.com/devops/optimizing-intellitrace-collection-on-production-server/).

 Voici quelques méthodes permettant d’obtenir le maximum de données sans ralentir votre application :

- Exécutez le collecteur uniquement si vous soupçonnez un problème ou si vous pouvez reproduire le problème.

   Démarrez la collecte, reproduisez le problème, puis arrêtez la collecte. Ouvrez le fichier .iTrace dans Visual Studio Enterprise et examinez les données. Consultez [Ouvrez le fichier .iTrace dans Visual Studio Enterprise](#BKMK_View_IntelliTrace_Log_Files).

- Pour les applications web et SharePoint, le collecteur enregistre les données pour chaque application partageant le pool d’applications spécifié. La collecte peut donc ralentir n’importe quelle application partageant le même pool d’applications, même si vous choisissez de limiter la collecte aux modules d’une seule application dans un plan de collecte.

   Pour empêcher le collecteur de ralentir d’autres applications, hébergez chaque application dans son propre pool d’applications.

- Passez en revue les événements du plan de collecte pour lesquels IntelliTrace collecte des données. Modifiez le plan de collecte en y désactivant les événements qui ne sont pas pertinents ou qui ne vous intéressent pas.

   Pour désactiver un événement, définissez l’attribut `enabled` pour l’élément `<DiagnosticEventSpecification>` avec la valeur `false`:

   `<DiagnosticEventSpecification enabled="false">`

   Si l’attribut `enabled` n’existe pas, l’événement est activé.

   *Comment cela améliore-t-il les performances ?*

  - Réduisez le temps de démarrage en désactivant les événements qui ne sont pas pertinents pour l’application. Par exemple, désactivez les événements Windows Workflow pour les applications qui n’utilisent pas Windows Workflow.

  - Vous pouvez améliorer les performances de démarrage et d’exécution en désactivant les événements de Registre pour les applications qui accèdent au registre, mais qui n’affichent pas de problèmes avec les paramètres du Registre.

- Passez en revue les modules du plan de collecte pour lesquels IntelliTrace collecte des données. Modifiez le plan de collecte en y incluant seulement les modules qui vous intéressent :

  1. Ouvrez le plan de collecte. Recherchez l’élément `<ModuleList>`.

  2. Dans `<ModuleList>`, définissez l’attribut `isExclusionList` avec la valeur `false`.

  3. Utilisez l’élément `<Name>` pour spécifier chaque module avec un des éléments suivants : nom de fichier, valeur de chaîne pour inclure un module dont le nom contient cette chaîne, ou clé publique.

     Par exemple, pour collecter uniquement des données du module web principal pour l’application web Fabrikam Fiber, créez une liste comme celle-ci :

  ```xml
  <ModuleList isExclusionList="false">
     <Name>FabrikamFiber.Web.dll</Name>
  </ModuleList>
  ```

   Pour collecter des données d’un module dont le nom inclut « Fabrikam », créez une liste comme celle-ci :

  ```xml
  <ModuleList isExclusionList="false">
     <Name>Fabrikam</Name>
  </ModuleList>
  ```

   Pour collecter des données de modules en spécifiant leurs jetons de clé publique, créez une liste comme celle-ci :

  ```xml
  <ModuleList isExclusionList="false">
     <Name>PublicKeyToken:B77A5C561934E089</Name>
     <Name>PublicKeyToken:B03F5F7F11D50A3A</Name>
     <Name>PublicKeyToken:31BF3856AD364E35</Name>
     <Name>PublicKeyToken:89845DCD8080CC91</Name>
     <Name>PublicKeyToken:71E9BCE111E9429C</Name>
  </ModuleList>
  ```

   *Comment cela améliore-t-il les performances ?*

   Cela réduit la quantité d’informations sur les appels de méthode et autres données d’instrumentation qu’IntelliTrace collecte quand l’application démarre et s’exécute. Avec ces données, vous pouvez :

  - parcourir le code après la collecte des données ;

  - examiner les valeurs passées aux appels de fonction et les valeurs de retour correspondantes.

    *Pourquoi ne pas exclure des modules à la place ?*

    Par défaut, les plans de collecte excluent les modules en définissant l’attribut `isExclusionList` avec la valeur `true`. Toutefois, malgré l’exclusion des modules, il est possible que des données soient collectées dans des modules qui ne répondent pas aux critères de la liste d’exclusion ou qui ne vous intéressent pas (par exemple, les modules tiers ou open source).

- *Y a-t-il des données qu’IntelliTrace ne collecte pas ?*

   Oui. Pour réduire l’impact sur les performances, IntelliTrace limite la collecte des données aux valeurs de types de données primitives qui sont passées à et retournées par les méthodes ainsi qu’aux valeurs de types de données primitives dans les champs sur les objets de niveau supérieur qui sont passés à et retournés par les méthodes.

   Par exemple, supposons que vous avez une signature de méthode `AlterEmployee` qui accepte un `id` entier et un objet `Employee``oldemployee`:

   `public Employee AlterEmployee(int id, Employee oldemployee)`

   Le type `Employee` a les attributs suivants : `Id`, `Name`et `HomeAddress`. Une relation d’association existe entre `Employee` et le type `Address` .

   ![Relations entre employés et adresse](../debugger/media/employeeaddressrelationship.png "EmployeeAddressRelationship")

   Le collecteur enregistre les valeurs pour `id`, `Employee.Id`, `Employee.Name` et l’objet `Employee` retourné par la méthode `AlterEmployee` . Toutefois, le collecteur n’enregistre pas d’informations sur l’objet `Address` (il indique seulement si cet objet a ou non une valeur null). Le collecteur n’enregistre pas non plus de données sur les variables locales de la méthode `AlterEmployee` , sauf si d’autres méthodes utilisent ces variables locales en tant que paramètres (elles sont alors enregistrées en tant que paramètres de méthode).

## <a name="where-else-can-i-get-intellitrace-data"></a><a name="WhereElse"></a> Où puis-je récupérer des données IntelliTrace ?

Vous pouvez récupérer des données IntelliTrace à partir d’une session de débogage IntelliTrace dans Visual Studio Enterprise. Consultez [fonctionnalités IntelliTrace](../debugger/intellitrace-features.md).

## <a name="where-can-i-get-more-information"></a>Où puis-je obtenir plus d'informations ?
 [Utilisation des données IntelliTrace enregistrées](../debugger/using-saved-intellitrace-data.md)

 [IntelliTrace](../debugger/intellitrace.md)

### <a name="blogs"></a>Blogs
 [Utilisation du collecteur autonome IntelliTrace à distance](https://devblogs.microsoft.com/devops/using-the-intellitrace-standalone-collector-remotely/)

 [Créer et personnaliser des plans de collecte IntelliTrace](https://devblogs.microsoft.com/devops/modifying-an-intellitrace-collection-plan-for-the-stand-alone-collector/)

 [Optimisation de la collecte IntelliTrace sur les serveurs de production](https://devblogs.microsoft.com/devops/optimizing-intellitrace-collection-on-production-server/)

 [Microsoft DevOps](https://devblogs.microsoft.com/devops/)

### <a name="forums"></a>Forums
 [Débogueur Visual Studio](https://social.msdn.microsoft.com/Forums/en-US/home)

### <a name="videos"></a>Vidéos
 [Vidéo Channel 9 : Collecte et analyse des données dans l’environnement de production](https://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Collecting-and-analyzing-data-in-production)
