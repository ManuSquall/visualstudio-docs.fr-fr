---
title: Configurer les rôles pour un service cloud Azure avec Visual Studio | Microsoft Docs
description: Découvrez comment installer et configurer des rôles pour les services cloud Azure à l’aide de Visual Studio.
author: ghogen
manager: douge
assetId: d397ef87-64e5-401a-aad5-7f83f1022e16
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 03/21/2017
ms.author: ghogen
ms.openlocfilehash: ce2259debb55c4792c2998f0e67df69dbc8cb7f9
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2018
ms.locfileid: "51002090"
---
# <a name="configure-azure-cloud-service-roles-with-visual-studio"></a>Configurer des rôles de services cloud Azure avec Visual Studio
Un service cloud Azure peut avoir un ou plusieurs rôles de web ou de travail. Pour chaque rôle, vous devez définir la façon dont ce rôle est configuré et également configurer la façon dont ce rôle s’exécute. Pour en savoir plus sur les rôles dans les services cloud, regardez la vidéo [présentation d’Azure Cloud Services](https://channel9.msdn.com/Series/Windows-Azure-Cloud-Services-Tutorials/Introduction-to-Windows-Azure-Cloud-Services). 

Les informations de votre service cloud sont stockées dans les fichiers suivants :

- **ServiceDefinition.csdef** -le fichier de définition de service définit les paramètres d’exécution pour votre service cloud, y compris les rôles requis, points de terminaison et taille de machine virtuelle. Aucune des données stockées dans `ServiceDefinition.csdef` peut être modifiée lorsque votre rôle est en cours d’exécution.
- **ServiceConfiguration.cscfg** : le fichier de configuration de service configure le nombre d’instances d’un rôle est exécutées et les valeurs des paramètres définis pour un rôle. Les données stockées dans `ServiceConfiguration.cscfg` peut être modifié pendant l’exécution de votre rôle.

Pour stocker des valeurs différentes pour les paramètres qui contrôlent la façon dont un rôle s’exécute, vous pouvez définir plusieurs configurations de service. Vous pouvez utiliser une configuration de service différents pour chaque environnement de déploiement. Par exemple, vous pouvez définir votre chaîne de connexion de compte de stockage à utiliser l’émulateur de stockage Azure local dans une configuration de service local et créer une autre configuration de service pour utiliser le stockage Azure dans le cloud.

Lorsque vous créez un service cloud Azure dans Visual Studio, deux configurations de service sont automatiquement créées et ajoutées à votre projet Azure :

- `ServiceConfiguration.Cloud.cscfg`
- `ServiceConfiguration.Local.cscfg`

## <a name="configure-an-azure-cloud-service"></a>Configurer un service cloud Azure
Vous pouvez configurer un service cloud Azure à partir de l’Explorateur de solutions dans Visual Studio, comme indiqué dans les étapes suivantes :

1. Créez ou ouvrez un projet de service cloud Azure dans Visual Studio.

1. Dans **l’Explorateur de solutions**, cliquez sur le projet, puis, dans le menu contextuel, sélectionnez **propriétés**.
   
    ![Menu de contexte de projet d’Explorateur de solutions](./media/vs-azure-tools-configure-roles-for-cloud-service/solution-explorer-project-context-menu.png)

1. Dans la page de propriétés du projet, sélectionnez le **développement** onglet. 

    ![Page de propriétés de projet - onglet développement](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-development-tab.png)

1. Dans le **Configuration du Service** liste, sélectionnez le nom de la configuration de service que vous souhaitez modifier. (Si vous souhaitez apporter des modifications à toutes les configurations de service pour ce rôle, sélectionnez **toutes les Configurations**.)
   
    > [!IMPORTANT]
    > Si vous choisissez une configuration de service spécifique, certaines propriétés sont désactivées, car elles peuvent uniquement être définies pour toutes les configurations. Pour modifier ces propriétés, vous devez sélectionner **toutes les Configurations**.
    > 
    > 
   
    ![Liste de Configuration du service pour un service cloud Azure](./media/vs-azure-tools-configure-roles-for-cloud-service/cloud-service-service-configuration-property.png)

## <a name="change-the-number-of-role-instances"></a>Modifier le nombre d’instances de rôle
Pour améliorer les performances de votre service cloud, vous pouvez modifier le nombre d’instances d’un rôle qui sont en cours d’exécution, en fonction du nombre d’utilisateurs ou de la charge attendue pour un rôle particulier. Une machine virtuelle distincte est créée pour chaque instance d’un rôle lorsque le service cloud s’exécute dans Azure. Cela affecte la facturation pour le déploiement de ce service cloud. Pour plus d’informations sur la facturation, consultez [comprendre votre facture Microsoft Azure](/azure/billing/billing-understand-your-bill).

1. Créez ou ouvrez un projet de service cloud Azure dans Visual Studio.

1. Dans **l’Explorateur de solutions**, développez le nœud du projet. Sous le **rôles** nœud, cliquez sur le rôle que vous souhaitez mettre à jour, puis, dans le menu contextuel, sélectionnez **propriétés**.

    ![Menu contextuel de rôle de l’Explorateur Azure solutions](./media/vs-azure-tools-configure-roles-for-cloud-service/solution-explorer-azure-role-context-menu.png)

1. Sélectionnez le **Configuration** onglet.

    ![Onglet Configuration](./media/vs-azure-tools-configure-roles-for-cloud-service/role-configuration-properties-page.png)

1. Dans le **Configuration du Service** liste, sélectionnez la configuration de service que vous souhaitez mettre à jour.
   
    ![Liste Configuration du service](./media/vs-azure-tools-configure-roles-for-cloud-service/role-configuration-properties-page-select-configuration.png)

1. Dans le **nombre d’instances** texte, entrez le nombre d’instances que vous souhaitez démarrer pour ce rôle. Chaque instance s’exécute sur une machine virtuelle séparée lorsque vous publiez le service cloud sur Azure.

    ![Le nombre d’instances de la mise à jour](./media/vs-azure-tools-configure-roles-for-cloud-service/role-configuration-properties-page-instance-count.png)

1. À partir de Visual Studio, barre d’outils, sélectionnez **enregistrer**.

## <a name="manage-connection-strings-for-storage-accounts"></a>Gérer les chaînes de connexion pour les comptes de stockage
Vous pouvez ajouter, supprimer ou modifier des chaînes de connexion pour vos configurations de service. Par exemple, vous pouvez vouloir une chaîne de connexion locale pour une configuration de service local qui a une valeur de `UseDevelopmentStorage=true`. Vous souhaiterez également configurer une configuration de service cloud qui utilise un compte de stockage dans Azure.

> [!WARNING]
> Lorsque vous entrez les informations de clé de compte de stockage Azure pour une chaîne de connexion de compte de stockage, ces informations sont stockées localement dans le fichier de configuration de service. Toutefois, ces informations ne sont actuellement pas stockées sous forme de texte chiffré.
> 
> 

En utilisant une valeur différente pour chaque configuration de service, il est inutile d’utiliser différentes chaînes de connexion dans votre service cloud ou de modifier votre code lorsque vous publiez votre service cloud sur Azure. Vous pouvez utiliser le même nom pour la chaîne de connexion dans votre code et la valeur est différente, selon la configuration de service que vous sélectionnez lorsque vous générez votre service cloud ou quand vous le publiez.

1. Créez ou ouvrez un projet de service cloud Azure dans Visual Studio.

1. Dans **l’Explorateur de solutions**, développez le nœud du projet. Sous le **rôles** nœud, cliquez sur le rôle que vous souhaitez mettre à jour, puis, dans le menu contextuel, sélectionnez **propriétés**.

    ![Menu contextuel de rôle de l’Explorateur Azure solutions](./media/vs-azure-tools-configure-roles-for-cloud-service/solution-explorer-azure-role-context-menu.png)

1. Sélectionnez le **paramètres** onglet.

    ![Onglet Paramètres](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab.png)

1. Dans le **Configuration du Service** liste, sélectionnez la configuration de service que vous souhaitez mettre à jour.

    ![Configuration du service](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-select-configuration.png)

1. Pour ajouter une chaîne de connexion, sélectionnez **ajouter un paramètre**.

    ![Ajouter la chaîne de connexion](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-add-setting.png)

1. Une fois que le nouveau paramètre a été ajouté à la liste, mettez à jour la ligne dans la liste avec les informations nécessaires.

    ![Nouvelle chaîne de connexion](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-add-setting-new-setting.png)

    - **Nom** -Entrez le nom que vous souhaitez utiliser pour la chaîne de connexion.
    - **Type** : sélectionnez **chaîne de connexion** dans la liste déroulante.
    - **Valeur** -vous pouvez entrer la chaîne de connexion directement dans le **valeur** de cellule, ou sélectionnez les points de suspension (...) pour travailler le **créer une chaîne de connexion stockage** boîte de dialogue.  

1. Dans le **créer une chaîne de connexion stockage** boîte de dialogue, sélectionnez une option pour **se connecter à l’aide de**. Puis suivez les instructions pour l’option sélectionnée :

    - **Émulateur de stockage Microsoft Azure** -si vous sélectionnez cette option, les autres paramètres de la boîte de dialogue sont désactivées car elles s’appliquent uniquement à Azure. Sélectionnez **OK**.
    - **Votre abonnement** : Si vous sélectionnez cette option, utilisez la liste déroulante pour sélectionner et de vous connecter à un compte Microsoft, ou ajouter un compte Microsoft. Sélectionnez un compte de stockage et d’abonnement Azure. Sélectionnez **OK**.
    - **Entrées manuellement les informations d’identification** -Entrez le nom de compte de stockage et la clé primaire ou secondaire. Sélectionnez une option pour **connexion** (HTTPS est recommandée pour la plupart des scénarios.) Sélectionnez **OK**.

1. Pour supprimer une chaîne de connexion, sélectionnez la chaîne de connexion, puis **supprimer un paramètre**.

1. À partir de Visual Studio, barre d’outils, sélectionnez **enregistrer**.

## <a name="programmatically-access-a-connection-string"></a>Accéder par programme à une chaîne de connexion

Les étapes suivantes montrent comment accéder par programme à une chaîne de connexion en utilisant C#.

1. Ajoutez le code suivant à l’aide des directives pour une C# où vous vous apprêtez à utiliser le paramètre de fichier :

    ```csharp
    using Microsoft.WindowsAzure;
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.ServiceRuntime;
    ```

1. Le code suivant illustre un exemple montrant comment accéder à une chaîne de connexion. Remplacez le &lt;ConnectionStringName > espace réservé avec la valeur appropriée. 

    ```csharp
    // Setup the connection to Azure Storage
    var storageAccount = CloudStorageAccount.Parse(RoleEnvironment.GetConfigurationSettingValue("<ConnectionStringName>"));
    ```

## <a name="add-custom-settings-to-use-in-your-azure-cloud-service"></a>Ajouter des paramètres personnalisés à utiliser dans votre service cloud Azure
Paramètres personnalisés dans le fichier de configuration de service vous permettent d’ajouter un nom et une valeur pour une chaîne pour une configuration de service spécifique. Vous pouvez choisir d’utiliser ce paramètre pour configurer une fonctionnalité dans votre service cloud en lisant la valeur du paramètre et de l’utilisation de cette valeur pour contrôler la logique dans votre code. Vous pouvez modifier ces valeurs de configuration de service sans avoir à reconstruire votre package de services ou lorsque votre service cloud est en cours d’exécution. Votre code peut vérifier les notifications de lorsqu’un paramètre est modifié. Consultez [événement RoleEnvironment.Changing](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleenvironment.changing.aspx).

Vous pouvez ajouter, supprimer ou modifier des paramètres personnalisés pour vos configurations de service. Vous pouvez vouloir différentes valeurs pour ces chaînes pour différentes configurations de service.

En utilisant une valeur différente pour chaque configuration de service, il est inutile utiliser des chaînes différentes dans votre service cloud ou de modifier votre code lorsque vous publiez votre service cloud sur Azure. Vous pouvez utiliser le même nom pour la chaîne dans votre code et la valeur est différente, selon la configuration de service que vous sélectionnez lorsque vous générez votre service cloud ou quand vous le publiez.

1. Créez ou ouvrez un projet de service cloud Azure dans Visual Studio.

1. Dans **l’Explorateur de solutions**, développez le nœud du projet. Sous le **rôles** nœud, cliquez sur le rôle que vous souhaitez mettre à jour, puis, dans le menu contextuel, sélectionnez **propriétés**.

    ![Menu contextuel de rôle de l’Explorateur Azure solutions](./media/vs-azure-tools-configure-roles-for-cloud-service/solution-explorer-azure-role-context-menu.png)

1. Sélectionnez le **paramètres** onglet.

    ![Onglet Paramètres](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab.png)

1. Dans le **Configuration du Service** liste, sélectionnez la configuration de service que vous souhaitez mettre à jour.

    ![Liste Configuration du service](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-select-configuration.png)

1. Pour ajouter un paramètre personnalisé, sélectionnez **ajouter un paramètre**.

    ![Ajouter un paramètre personnalisé](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-add-setting.png)

1. Une fois que le nouveau paramètre a été ajouté à la liste, mettez à jour la ligne dans la liste avec les informations nécessaires.

    ![Nouveau paramètre personnalisé](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-add-setting-new-setting.png)

    - **Nom** -Entrez le nom du paramètre.
    - **Type** : sélectionnez **chaîne** dans la liste déroulante.
    - **Valeur** -Entrez la valeur du paramètre. Vous pouvez entrer la valeur directement dans le **valeur** de cellule, ou sélectionnez les points de suspension (...) pour entrer la valeur dans le **modification de la chaîne** boîte de dialogue.  

1. Pour supprimer un paramètre personnalisé, sélectionnez le paramètre, puis **supprimer un paramètre**.

1. À partir de Visual Studio, barre d’outils, sélectionnez **enregistrer**.

## <a name="programmatically-access-a-custom-settings-value"></a>Accès par programme la valeur d’un paramètre personnalisé
 
Les étapes suivantes montrent comment accéder par programme à un paramètre personnalisé à l’aide C#.

1. Ajoutez le code suivant à l’aide des directives pour une C# où vous vous apprêtez à utiliser le paramètre de fichier :

    ```csharp
    using Microsoft.WindowsAzure;
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.ServiceRuntime;
    ```

1. Le code suivant illustre un exemple montrant comment accéder à un paramètre personnalisé. Remplacez le &lt;SettingName > espace réservé avec la valeur appropriée. 
    
    ```csharp
    var settingValue = RoleEnvironment.GetConfigurationSettingValue("<SettingName>");
    ```

## <a name="manage-local-storage-for-each-role-instance"></a>Gérer le stockage local pour chaque instance de rôle
Vous pouvez ajouter le stockage de système de fichiers local pour chaque instance d’un rôle. Les données stockées dans la mesure où le stockage n’est pas accessible par d’autres instances du rôle pour lequel les données sont stockées, ni aux autres rôles.  

1. Créez ou ouvrez un projet de service cloud Azure dans Visual Studio.

1. Dans **l’Explorateur de solutions**, développez le nœud du projet. Sous le **rôles** nœud, cliquez sur le rôle que vous souhaitez mettre à jour, puis, dans le menu contextuel, sélectionnez **propriétés**.

    ![Menu contextuel de rôle de l’Explorateur Azure solutions](./media/vs-azure-tools-configure-roles-for-cloud-service/solution-explorer-azure-role-context-menu.png)

1. Sélectionnez le **stockage Local** onglet.

    ![Onglet stockage local](./media/vs-azure-tools-configure-roles-for-cloud-service/role-local-storage-tab.png)

1. Dans le **Configuration du Service** liste, vérifiez que **toutes les Configurations** est sélectionné comme les paramètres de stockage local s’appliquent à toutes les configurations de service. Toute autre valeur génère tous les champs d’entrée dans la page en cours de désactivation. 

    ![Liste Configuration du service](./media/vs-azure-tools-configure-roles-for-cloud-service/role-local-storage-tab-service-configuration.png)

1. Pour ajouter une entrée de stockage local, sélectionnez **ajouter le stockage Local**.

    ![Ajouter un stockage local](./media/vs-azure-tools-configure-roles-for-cloud-service/role-local-storage-tab-add-local-storage.png)

1. Une fois que la nouvelle entrée de stockage local a été ajoutée à la liste, mettez à jour la ligne dans la liste avec les informations nécessaires.

    ![Nouvelle entrée de stockage local](./media/vs-azure-tools-configure-roles-for-cloud-service/role-local-storage-tab-new-local-storage.png)

    - **Nom** -Entrez le nom que vous souhaitez utiliser pour le nouveau stockage local.
    - **Taille (Mo)** -Entrez la taille en Mo dont vous avez besoin pour le nouveau stockage local.
    - **Le nettoyage sur le recyclage des rôles** -Sélectionnez cette option pour supprimer les données dans le nouveau stockage local lorsque l’ordinateur virtuel pour le rôle est recyclé.

1. Pour supprimer une entrée de stockage local, sélectionnez l’entrée, puis **supprimer le stockage Local**.

1. À partir de Visual Studio, barre d’outils, sélectionnez **enregistrer**.

## <a name="programmatically-accessing-local-storage"></a>Accès par programme au stockage local

Cette section montre comment accéder par programme à l’aide du stockage local C# en écrivant un fichier texte de test `MyLocalStorageTest.txt`.  

### <a name="write-a-text-file-to-local-storage"></a>Écrire un fichier texte dans le stockage local

Le code suivant montre un exemple montrant comment écrire un fichier texte dans le stockage local. Remplacez le &lt;LocalStorageName > espace réservé avec la valeur appropriée. 

    ```csharp
    // Retrieve an object that points to the local storage resource
    LocalResource localResource = RoleEnvironment.GetLocalResource("<LocalStorageName>");
    
    //Define the file name and path
    string[] paths = { localResource.RootPath, "MyLocalStorageTest.txt" };
    String filePath = Path.Combine(paths);
    
    using (FileStream writeStream = File.Create(filePath))
    {
        Byte[] textToWrite = new UTF8Encoding(true).GetBytes("Testing Web role storage");
        writeStream.Write(textToWrite, 0, textToWrite.Length);
    }

    ```

### <a name="find-a-file-written-to-local-storage"></a>Rechercher un fichier écrit dans le stockage local

Pour afficher le fichier créé par le code dans la section précédente, procédez comme suit :
    
1.  Dans la zone de notification Windows, cliquez sur l’icône Windows Azure et, dans le menu contextuel, sélectionnez **Show Compute Emulator UI**. 

    ![Afficher l’émulateur de calcul Azure](./media/vs-azure-tools-configure-roles-for-cloud-service/show-compute-emulator.png)

1. Sélectionnez le rôle web.

    ![Émulateur de calcul Azure](./media/vs-azure-tools-configure-roles-for-cloud-service/compute-emulator.png)

1. Sur le **émulateur de calcul Azure Microsoft** menu, sélectionnez **outils** > **ouvrir magasin local**.

    ![Élément de menu Ouvrir magasin local](./media/vs-azure-tools-configure-roles-for-cloud-service/compute-emulator-open-local-store-menu.png)

1. Lorsque la fenêtre de l’Explorateur Windows s’ouvre, entrez « MyLocalStorageTest.txt » dans le **recherche** zone de texte, puis sélectionnez **entrée** pour démarrer la recherche. 

## <a name="next-steps"></a>Étapes suivantes
En savoir plus sur les projets Azure dans Visual Studio en lisant [configuration d’un projet Azure](vs-azure-tools-configuring-an-azure-project.md). En savoir plus sur le schéma de service cloud en lisant [référence du schéma](https://msdn.microsoft.com/library/azure/dd179398).

