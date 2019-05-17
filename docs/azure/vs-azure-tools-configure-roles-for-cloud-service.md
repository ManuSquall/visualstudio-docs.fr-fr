---
title: Configurer les rôles d’un service cloud Azure
description: Découvrez comment installer et configurer des rôles pour les services cloud Azure à l’aide de Visual Studio.
author: ghogen
manager: jillfra
assetId: d397ef87-64e5-401a-aad5-7f83f1022e16
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 03/21/2017
ms.author: ghogen
ms.openlocfilehash: 86a86a097bc5e9d3cd567502ec94aae3cbafd324
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62552322"
---
# <a name="configure-azure-cloud-service-roles-with-visual-studio"></a>Configurer des rôles de service cloud Azure avec Visual Studio
Un service cloud Azure peut avoir un ou plusieurs rôles de travail ou rôles web. Pour chaque rôle, vous devez définir le mode de configuration de ce rôle et configurer son mode d’exécution. Pour en savoir plus sur les rôles dans les services cloud, regardez la vidéo [Introduction aux services cloud Azure](https://channel9.msdn.com/Series/Windows-Azure-Cloud-Services-Tutorials/Introduction-to-Windows-Azure-Cloud-Services).

Les informations pour votre service cloud sont stockées dans les fichiers suivants :

- **ServiceDefinition.csdef** : le fichier de définition de service définit les paramètres d’exécution de votre service cloud, y compris les rôles requis, les points de terminaison et la taille de la machine virtuelle. Aucune des données stockées dans `ServiceDefinition.csdef` ne peut être modifiée lorsque votre rôle est en cours d’exécution.
- **ServiceConfiguration.cscfg** : le fichier de configuration de service configure le nombre d’instances d’un rôle exécutées et les valeurs des paramètres définis pour un rôle. Les données stockées dans `ServiceConfiguration.cscfg` peuvent être modifiées lorsque votre rôle est en cours d’exécution.

Pour stocker différentes valeurs pour les paramètres qui contrôlent l’exécution d’un rôle, vous pouvez définir plusieurs configurations de service. Vous pouvez utiliser une configuration de service différente pour chaque environnement de déploiement. Par exemple, vous pouvez définir votre chaîne de connexion de compte de stockage pour utiliser l’émulateur de stockage Azure local dans une configuration de service local et créer une autre configuration de service pour utiliser le stockage Azure dans le cloud.

Lorsque vous créez un service cloud Azure dans Visual Studio, deux configurations de service sont automatiquement créées et ajoutées à votre projet Azure :

- `ServiceConfiguration.Cloud.cscfg`
- `ServiceConfiguration.Local.cscfg`

## <a name="configure-an-azure-cloud-service"></a>Configurer un service cloud Azure
Vous pouvez configurer un service cloud Azure à partir de l’Explorateur de solutions dans Visual Studio, comme indiqué dans les étapes suivantes :

1. Créez ou ouvrez un projet de service cloud Azure dans Visual Studio.

1. Dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur le projet, puis, dans le menu contextuel, sélectionnez **Propriétés**.

    ![Menu contextuel de projet dans l’Explorateur de solutions](./media/vs-azure-tools-configure-roles-for-cloud-service/solution-explorer-project-context-menu.png)

1. Dans la page de propriétés du projet, sélectionnez l’onglet **Développement**.

    ![Page de propriétés du projet : onglet développement](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-development-tab.png)

1. Dans la liste **Configuration du service**, sélectionnez le nom de la configuration de service que vous souhaitez modifier. (Si vous souhaitez modifier toutes les configurations de service pour ce rôle, sélectionnez **Toutes les configurations**.)

    > [!IMPORTANT]
    > Si vous choisissez une configuration de service spécifique, certaines propriétés sont désactivées parce qu’elles peuvent être définies uniquement pour toutes les configurations. Pour modifier ces propriétés, vous devez sélectionner **Toutes les configurations**.
    >
    >

    ![Liste Configuration du service pour un service cloud Azure](./media/vs-azure-tools-configure-roles-for-cloud-service/cloud-service-service-configuration-property.png)

## <a name="change-the-number-of-role-instances"></a>Modifier le nombre d’instances d’un rôle
Pour améliorer la performance de votre service cloud, vous pouvez modifier le nombre d’instances d’un rôle qui s’exécutent, en fonction du nombre d’utilisateurs ou de la charge attendue pour un rôle particulier. Une machine virtuelle distincte est créée pour chaque instance d’un rôle quand le service cloud s’exécute dans Azure. Cela affecte la facturation correspondant au déploiement de ce service cloud. Pour plus d’informations sur la facturation, consultez [Comprendre votre facture Microsoft Azure](/azure/billing/billing-understand-your-bill).

1. Créez ou ouvrez un projet de service cloud Azure dans Visual Studio.

1. Dans **l’Explorateur de solutions**, développez le nœud du projet. Sous le nœud **Rôles**, cliquez avec le bouton droit sur le rôle que vous souhaitez mettre à jour, puis, dans le menu contextuel, sélectionnez **Propriétés**.

    ![Menu contextuel de rôle Azure dans l’Explorateur de solutions](./media/vs-azure-tools-configure-roles-for-cloud-service/solution-explorer-azure-role-context-menu.png)

1. Sélectionnez l’onglet **Configuration**.

    ![Onglet Configuration](./media/vs-azure-tools-configure-roles-for-cloud-service/role-configuration-properties-page.png)

1. Dans la liste **Configuration du service**, sélectionnez la configuration de service que vous voulez mettre à jour.

    ![Liste Configuration du service](./media/vs-azure-tools-configure-roles-for-cloud-service/role-configuration-properties-page-select-configuration.png)

1. Dans la zone de texte **Nombre d’instances** , entrez le nombre d’instances que vous voulez démarrer pour ce rôle. Chaque instance s’exécute sur une machine virtuelle distincte quand vous publiez le service cloud sur Azure.

    ![Mise à jour du nombre d’instances](./media/vs-azure-tools-configure-roles-for-cloud-service/role-configuration-properties-page-instance-count.png)

1. Dans la barre d’outils de Visual Studio, sélectionnez **Enregistrer**.

## <a name="manage-connection-strings-for-storage-accounts"></a>Gérer des chaînes de connexion pour des comptes de stockage
Vous pouvez ajouter, supprimer ou modifier des chaînes de connexion pour vos configurations de service. Par exemple, vous pouvez vouloir une chaîne de connexion locale pour une configuration de service local qui a pour valeur `UseDevelopmentStorage=true`. Vous pouvez aussi vouloir définir une configuration de service cloud qui utilise un compte de stockage dans Azure.

> [!WARNING]
> Lorsque vous entrez les informations de clé du compte de stockage Azure pour une chaîne de connexion de compte de stockage, ces informations sont stockées localement dans le fichier de configuration de service. Toutefois, ces informations ne sont pas stockées sous forme de texte chiffré pour le moment.
>
>

Si vous utilisez une valeur différente pour chaque configuration de service, il n’est pas nécessaire d’utiliser des chaînes de connexion différentes dans votre service cloud ni de modifier votre code quand vous publiez votre service cloud sur Azure. Vous pouvez utiliser le même nom pour la chaîne de connexion dans votre code, et la valeur sera différente, en fonction de la configuration de service que vous sélectionnez quand vous générez votre service cloud ou quand vous le publiez.

1. Créez ou ouvrez un projet de service cloud Azure dans Visual Studio.

1. Dans **l’Explorateur de solutions**, développez le nœud du projet. Sous le nœud **Rôles**, cliquez avec le bouton droit sur le rôle que vous souhaitez mettre à jour, puis, dans le menu contextuel, sélectionnez **Propriétés**.

    ![Menu contextuel de rôle Azure dans l’Explorateur de solutions](./media/vs-azure-tools-configure-roles-for-cloud-service/solution-explorer-azure-role-context-menu.png)

1. Sélectionnez l’onglet **Paramètres**.

    ![Onglet Paramètres](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab.png)

1. Dans la liste **Configuration du service**, sélectionnez la configuration de service que vous voulez mettre à jour.

    ![Configuration du service](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-select-configuration.png)

1. Pour ajouter une chaîne de connexion, sélectionnez **Ajouter un paramètre**.

    ![Ajouter une chaîne de connexion](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-add-setting.png)

1. Une fois le nouveau paramètre ajouté à la liste, mettez à jour la ligne dans la liste avec les informations nécessaires.

    ![New connection string](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-add-setting-new-setting.png)

    - **Nom** : entrez le nom que vous voulez utiliser pour la chaîne de connexion.
    - **Type** : sélectionnez **Chaîne de connexion** dans la liste déroulante.
    - **Valeur** : vous pouvez entrer la chaîne de connexion directement dans la cellule **Valeur** ou sélectionner les points de suspension (...) pour utiliser la boîte de dialogue **Créer une chaîne de connexion de stockage**.

1. Dans la boîte de dialogue **Créer une chaîne de connexion de stockage**, sélectionnez une option pour **Se connecter avec**. Suivez les instructions correspondant à l’option sélectionnée :

    - **Émulateur de stockage Microsoft Azure** : si vous sélectionnez cette option, les autres paramètres de la boîte de dialogue sont désactivés, car ils s’appliquent uniquement à Azure. Sélectionnez **OK**.
    - **Votre abonnement** : si vous sélectionnez cette option, utilisez la liste déroulante pour sélectionner un compte Microsoft et s’y connecter ou pour ajouter un compte Microsoft. Sélectionnez un abonnement et un compte de stockage Azure. Sélectionnez **OK**.
    - **Informations d’identification entrées manuellement** : entrez le nom du compte de stockage, ainsi que la clé primaire ou secondaire. Sélectionnez une option pour **Connexion** (le protocole HTTPS est recommandé pour la plupart des scénarios.) Sélectionnez **OK**.

1. Pour supprimer une chaîne de connexion, sélectionnez-la, puis sélectionnez **Supprimer un paramètre**.

1. Dans la barre d’outils de Visual Studio, sélectionnez **Enregistrer**.

## <a name="programmatically-access-a-connection-string"></a>Accéder par programme à une chaîne de connexion

Les étapes suivantes montrent comment accéder par programme à une chaîne de connexion en C#.

1. En utilisant les directives, ajoutez le contenu suivant dans un fichier en C# dans lequel vous allez utiliser le paramètre :

    ```csharp
    using Microsoft.WindowsAzure;
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.ServiceRuntime;
    ```

1. Le code suivant illustre un exemple d’accès à une chaîne de connexion. Remplacez l’espace réservé &lt;ConnectionStringName> par la valeur appropriée.

    ```csharp
    // Setup the connection to Azure Storage
    var storageAccount = CloudStorageAccount.Parse(RoleEnvironment.GetConfigurationSettingValue("<ConnectionStringName>"));
    ```

## <a name="add-custom-settings-to-use-in-your-azure-cloud-service"></a>Ajouter des paramètres personnalisés à utiliser dans votre service cloud Azure
Les paramètres personnalisés dans le fichier de configuration de service vous permettent d’ajouter un nom et une valeur pour une chaîne pour une configuration de service spécifique. Vous pouvez choisir d’utiliser ce paramètre pour configurer une fonctionnalité dans votre service cloud en lisant la valeur du paramètre et en utilisant cette valeur pour contrôler la logique de votre code. Vous pouvez modifier ces valeurs de configuration de service sans devoir régénérer votre package de services ou lorsque votre service cloud est en cours d’exécution. Votre code peut vérifier les notifications produites lorsqu’un paramètre est modifié. Consultez [RoleEnvironment.Changing Event](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleenvironment.changing.aspx).

Vous pouvez ajouter, supprimer ou modifier des paramètres personnalisés pour vos configurations de service. Vous pouvez vouloir différentes valeurs pour ces chaînes pour différentes configurations de service.

Si vous utilisez une valeur différente pour chaque configuration de service, il n’est pas nécessaire d’utiliser des chaînes différentes dans votre service cloud ni de modifier votre code quand vous publiez votre service cloud sur Azure. Vous pouvez utiliser le même nom pour la chaîne dans votre code et la valeur sera différente, en fonction de la configuration de service que vous sélectionnez quand vous générez votre service cloud ou quand vous le publiez.

1. Créez ou ouvrez un projet de service cloud Azure dans Visual Studio.

1. Dans **l’Explorateur de solutions**, développez le nœud du projet. Sous le nœud **Rôles**, cliquez avec le bouton droit sur le rôle que vous souhaitez mettre à jour, puis, dans le menu contextuel, sélectionnez **Propriétés**.

    ![Menu contextuel de rôle Azure dans l’Explorateur de solutions](./media/vs-azure-tools-configure-roles-for-cloud-service/solution-explorer-azure-role-context-menu.png)

1. Sélectionnez l’onglet **Paramètres**.

    ![Onglet Paramètres](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab.png)

1. Dans la liste **Configuration du service**, sélectionnez la configuration de service que vous voulez mettre à jour.

    ![Liste Configuration du service](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-select-configuration.png)

1. Pour ajouter un paramètre personnalisé, sélectionnez **Ajouter un paramètre**.

    ![Ajouter un paramètre personnalisé](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-add-setting.png)

1. Une fois le nouveau paramètre ajouté à la liste, mettez à jour la ligne dans la liste avec les informations nécessaires.

    ![Nouveau paramètre personnalisé](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-add-setting-new-setting.png)

    - **Nom** : entrez le nom du paramètre.
    - **Type** : sélectionnez **Chaîne** dans la liste déroulante.
    - **Valeur** : entrez la valeur du paramètre. Vous pouvez entrer directement la valeur dans la cellule **Valeur** ou sélectionner les points de suspension (...) pour entrer la valeur dans la boîte de dialogue **Modifier la chaîne**.

1. Pour supprimer un paramètre personnalisé, sélectionnez-le, puis sélectionnez **Supprimer un paramètre**.

1. Dans la barre d’outils de Visual Studio, sélectionnez **Enregistrer**.

## <a name="programmatically-access-a-custom-settings-value"></a>Accéder par programme à la valeur d’un paramètre personnalisé

Les étapes suivantes montrent comment accéder par programme à un paramètre personnalisé en C#.

1. En utilisant les directives, ajoutez le contenu suivant dans un fichier en C# dans lequel vous allez utiliser le paramètre :

    ```csharp
    using Microsoft.WindowsAzure;
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.ServiceRuntime;
    ```

1. Le code suivant illustre un exemple d’accès à un paramètre personnalisé. Remplacez l’espace réservé &lt;SettingName> par la valeur appropriée.

    ```csharp
    var settingValue = RoleEnvironment.GetConfigurationSettingValue("<SettingName>");
    ```

## <a name="manage-local-storage-for-each-role-instance"></a>Gérer le stockage local pour chaque instance de rôle
Vous pouvez ajouter le stockage de système de fichiers local pour chaque instance d’un rôle. Les données stockées dans cet espace de stockage ne sont pas accessibles aux autres instances du rôle pour lequel les données sont stockées ni aux autres rôles.

1. Créez ou ouvrez un projet de service cloud Azure dans Visual Studio.

1. Dans **l’Explorateur de solutions**, développez le nœud du projet. Sous le nœud **Rôles**, cliquez avec le bouton droit sur le rôle que vous souhaitez mettre à jour, puis, dans le menu contextuel, sélectionnez **Propriétés**.

    ![Menu contextuel de rôle Azure dans l’Explorateur de solutions](./media/vs-azure-tools-configure-roles-for-cloud-service/solution-explorer-azure-role-context-menu.png)

1. Sélectionnez l’onglet **Stockage local**.

    ![Onglet Stockage local](./media/vs-azure-tools-configure-roles-for-cloud-service/role-local-storage-tab.png)

1. Dans la liste **Configuration du service**, vérifiez que l’option **Toutes les configurations** est sélectionnée, car les paramètres de stockage local s’appliquent à toutes les configurations de service. Toute autre valeur entraîne la désactivation de tous les champs d’entrée de la page.

    ![Liste Configuration du service](./media/vs-azure-tools-configure-roles-for-cloud-service/role-local-storage-tab-service-configuration.png)

1. Pour ajouter une entrée de stockage local, sélectionnez **Ajouter le stockage local**.

    ![Ajouter le stockage local](./media/vs-azure-tools-configure-roles-for-cloud-service/role-local-storage-tab-add-local-storage.png)

1. Une fois la nouvelle entrée de stockage local ajoutée à la liste, mettez à jour la ligne dans la liste avec les informations nécessaires.

    ![Nouvelle entrée de stockage local](./media/vs-azure-tools-configure-roles-for-cloud-service/role-local-storage-tab-new-local-storage.png)

    - **Nom** : entrez le nom que vous voulez utiliser pour le nouveau stockage local.
    - **Taille (Mo)**  : entrez la taille (en Mo) dont vous avez besoin pour le nouveau stockage local.
    - **Nettoyer après le recyclage des rôles** : sélectionnez cette option pour supprimer les données dans le nouveau stockage local quand la machine virtuelle pour le rôle est recyclée.

1. Pour supprimer une entrée de stockage local, sélectionnez l’entrée, puis **Remove Local Storage (Supprimer le stockage local)**.

1. Dans la barre d’outils de Visual Studio, sélectionnez **Enregistrer**.

## <a name="programmatically-accessing-local-storage"></a>Accès par programme au stockage local

Cette section montre comment accéder par programme au stockage local en C# en écrivant un fichier texte de test `MyLocalStorageTest.txt`.

### <a name="write-a-text-file-to-local-storage"></a>Écrire un fichier texte dans le stockage local

Le code suivant présente un exemple d’écriture de fichier texte dans le stockage local. Remplacez l’espace réservé &lt;LocalStorageName> par la valeur appropriée.

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

1. Dans la zone de notification Windows, cliquez avec le bouton droit sur l’icône Azure, puis, dans le menu contextuel, sélectionnez **Afficher l’interface utilisateur de l’émulateur de calcul**.

    ![Afficher l’émulateur de calcul Azure](./media/vs-azure-tools-configure-roles-for-cloud-service/show-compute-emulator.png)

1. Sélectionnez le rôle web.

    ![Émulateur de calcul Azure](./media/vs-azure-tools-configure-roles-for-cloud-service/compute-emulator.png)

1. Dans le menu **Émulateur de calcul Microsoft Azure**, sélectionnez **Outils** > **Ouvrir magasin local**.

    ![Élément du menu Ouvrir magasin local](./media/vs-azure-tools-configure-roles-for-cloud-service/compute-emulator-open-local-store-menu.png)

1. Lorsque la fenêtre de l’Explorateur Windows s’ouvre, entrez « MyLocalStorageTest.txt » dans la zone de texte **Rechercher**, puis sélectionnez **Entrée** pour démarrer la recherche.

## <a name="next-steps"></a>Étapes suivantes
En savoir plus sur les projets Azure dans Visual Studio en lisant [Configuration d’un projet Azure](vs-azure-tools-configuring-an-azure-project.md). En savoir plus sur le schéma de service cloud en lisant [Référence de schéma](https://msdn.microsoft.com/library/azure/dd179398).
