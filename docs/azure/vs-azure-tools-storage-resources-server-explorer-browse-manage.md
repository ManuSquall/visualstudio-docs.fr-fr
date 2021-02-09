---
title: Parcourir et gérer les ressources de stockage
description: Consultation et gestion des ressources de stockage à l’aide de l’Explorateur de serveurs
ms.custom: SEO-VS-2020
author: ghogen
manager: jmartens
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 8/24/2017
ms.author: ghogen
ms.openlocfilehash: 70656b71df09f5635ebfb5d4532256e8f0d3dd35
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99843850"
---
# <a name="browse-and-manage-storage-resources-by-using-server-explorer"></a>Consulter et gérer les ressources de stockage à l’aide de l’Explorateur de serveurs

[!INCLUDE [storage-try-azure-tools](./includes/storage-try-azure-tools.md)]

## <a name="overview"></a>Vue d’ensemble

Si vous avez installé Azure Tools pour Microsoft Visual Studio, vous pouvez afficher les données relatives aux objets blob, aux files d’attente et aux tables à partir de vos comptes de stockage Azure. Dans Explorateur de serveurs, le nœud de **stockage** Azure affiche les données qui se trouvent dans votre compte d’émulateur de stockage local et dans vos autres comptes de stockage Azure.

Pour afficher les Explorateur de serveurs dans Visual Studio, dans la barre de menus, sélectionnez **Afficher** les  >  **Explorateur de serveurs**. Le nœud **Storage** affiche tous les comptes de stockage qui existent sous chaque abonnement ou certificat Azure auquel vous êtes connecté. Si votre compte de stockage n’apparaît pas, vous pouvez l’ajouter en suivant les instructions fournies [plus loin dans cet article](#add-storage-accounts-by-using-server-explorer).

À partir de la version 2.7 du SDK Azure, vous pouvez également utiliser Cloud Explorer pour afficher et gérer vos ressources Azure. Pour plus d’informations, consultez [gestion des ressources Azure avec Cloud Explorer](vs-azure-tools-resources-managing-with-cloud-explorer.md).

## <a name="view-and-manage-storage-resources-in-visual-studio"></a>Afficher et gérer les ressources de stockage dans Visual Studio

L’Explorateur de serveurs affiche automatiquement la liste des objets blob, des files d’attente et des tables de votre compte d’émulateur de stockage. Le compte de l’émulateur de stockage est listé dans Explorateur de serveurs sous le nœud de **stockage** en tant que nœud de **développement** .

Pour afficher les ressources du compte de l’émulateur de stockage, développez le nœud **Développement** . Si l’émulateur de stockage n’a pas encore été démarré quand vous développez le nœud **Développement**, il démarre automatiquement. Ce processus peut prendre plusieurs secondes. Vous pouvez continuer à travailler dans d’autres parties de Visual Studio pendant le démarrage de l’émulateur de stockage.

Pour afficher les ressources dans un compte de stockage, développez le nœud du compte de stockage dans l’Explorateur de serveurs pour afficher les nœuds **Objets blob**, **Files d'attente** et **Tables**.

## <a name="work-with-blob-resources"></a>Utilisation des ressources d’objets blob

Le nœud **Objets BLOB** affiche une liste de conteneurs pour le compte de stockage sélectionné. Les conteneurs d’objets blob contiennent des fichiers d’objets blob, que vous pouvez ranger dans des dossiers et des sous-dossiers. Pour plus d’informations, voir [Utilisation du stockage d’objets blob à partir de .NET](/azure/storage/blobs/storage-dotnet-how-to-use-blobs).

### <a name="to-create-a-blob-container"></a>Pour créer un conteneur d’objets blob

1. Ouvrez le menu contextuel du nœud **Objets blob**, puis sélectionnez **Créer un conteneur d’objets blob**.
1. Entrez le nom du nouveau conteneur dans la boîte de dialogue **Créer un conteneur d’objets blob**.
1. Sélectionnez Entrée sur votre clavier, ou cliquez/appuyez en dehors du champ de nom pour enregistrer le conteneur d’objets blob.

   > [!NOTE]
   > Le nom du conteneur d’objets blob doit commencer par un chiffre (0-9) ou une lettre minuscule (a-z).

### <a name="to-delete-a-blob-container"></a>Pour supprimer un conteneur d’objets blob

Ouvrez le menu contextuel du conteneur d’objets blob que vous voulez supprimer, puis sélectionnez **Supprimer**.

### <a name="to-display-a-list-of-the-items-in-a-blob-container"></a>Pour afficher la liste des éléments d’un conteneur d’objets blob

Ouvrez le menu contextuel d’un conteneur d’objets blob de la liste, puis sélectionnez **Ouvrir**.

Le contenu d’un conteneur d’objets blob s’affiche sous un onglet que l’on appelle vue du conteneur d’objets blob.

![Vue du conteneur d’objets blob](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC749016.png)

Vous pouvez effectuer les opérations suivantes sur les objets blob en utilisant les boutons situés dans l’angle supérieur droit de la vue du conteneur d’objets blob :

* Entrer une valeur de filtre et l’appliquer.
* Actualiser la liste des objets blob du conteneur.
* Chargez un fichier.
* Supprimer un objet blob. (Si vous supprimez un fichier du conteneur d’objets blob, le fichier sous-jacent n’est pas supprimé. Il est uniquement supprimé du conteneur d’objets blob.)
* Ouvrir un objet blob.
* Enregistrer un objet blob sur l’ordinateur local.

### <a name="to-create-a-folder-or-subfolder-in-a-blob-container"></a>Pour créer un dossier ou un sous-dossier dans un conteneur d’objets blob

1. Choisissez le conteneur d’objets BLOB dans **Cloud Explorer**. Dans la fenêtre du conteneur, sélectionnez le bouton **Charger l’objet blob**.

1. Dans la boîte de dialogue **Télécharger un nouveau fichier**, sélectionnez le bouton **Parcourir** pour spécifier le fichier à charger, puis entrez un nom de dossier dans la zone **Dossier (facultatif)**.

   ![Chargement d’un fichier dans un dossier d’objets blob](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC766037.png)

   Vous pouvez ajouter des sous-dossiers dans les dossiers du conteneur en suivant la même étape. Si vous ne spécifiez pas de nom de dossier, le fichier est chargé dans le niveau supérieur du conteneur d’objets blob. Le fichier apparaîtra dans le dossier spécifié du conteneur.

   ![Dossier ajouté à un conteneur d’objets blob](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC766038.png)

1. Double-cliquez sur le dossier ou sélectionnez Entrée pour afficher le contenu du dossier. Une fois le dossier ouvert, vous pouvez retourner à la racine du conteneur en sélectionnant le bouton **Ouvrir le répertoire parent** (flèche).

### <a name="to-delete-a-container-folder"></a>Pour supprimer un dossier du conteneur

Supprimez tous les fichiers du dossier.

Étant donné que les dossiers des conteneurs d’objets blob sont des dossiers virtuels, vous ne pouvez pas créer de dossier vide. Vous ne pouvez pas non plus supprimer un dossier pour supprimer le contenu de ses fichiers ; vous devez supprimer tout le contenu d'un dossier pour supprimer le dossier lui-même.

### <a name="to-filter-blobs-in-a-container"></a>Pour filtrer les objets blob d’un conteneur

Vous pouvez filtrer les objets blob qui sont affichés en spécifiant un préfixe commun.

Par exemple, si vous entrez le préfixe **hello** dans la zone de texte de filtre, puis sélectionnez le bouton **Exécuter** (**!**), seuls les objets blob qui commencent par « hello » s’affichent.

![Zone de texte de filtre](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC519076.png)

La zone de texte de filtre respecte la casse et ne prend pas en charge le filtrage à l’aide de caractères génériques. Les objets blob ne peuvent être filtrés que par préfixe. Le préfixe peut inclure un délimiteur si vous utilisez des délimiteurs pour organiser les objets blob en hiérarchie virtuelle. Par exemple, un filtrage à l’aide du préfixe « HelloFabric/ » retourne tous les objets blob qui commencent par cette chaîne.

### <a name="to-download-blob-data"></a>Pour télécharger les données des objets blob

Dans **Cloud Explorer**, utilisez l’une des méthodes suivantes :

* Ouvrez le menu contextuel pour un ou plusieurs objets blob, puis sélectionnez **Ouvrir**.
* Choisissez le nom de l’objet blob, puis sélectionnez le bouton **Ouvrir**.
* Double-cliquez sur le nom de l’objet blob.

La progression du téléchargement d'un objet blob s'affiche dans la fenêtre **Journal des activités Azure**.

L’objet blob s’ouvre dans l’éditeur par défaut pour ce type de fichier. Si le système d’exploitation reconnaît le type de fichier, le fichier s’ouvre dans une application installée localement. Dans le cas contraire, vous êtes invité à choisir une application qui est appropriée pour le type de fichier de l’objet blob. Le fichier local qui est créé quand vous téléchargez un objet blob est en lecture seule.

Les données d’objets blob sont mises en cache localement et vérifiées par rapport à l’heure de dernière modification de l’objet blob dans le stockage d’objets blob Azure. Si l’objet blob a été mis à jour depuis son dernier téléchargement, il est retéléchargé. Dans le cas contraire, l’objet blob est chargé à partir du disque local.

Par défaut, un objet blob est téléchargé dans un répertoire temporaire. Pour télécharger des objets blob dans un répertoire spécifique, ouvrez le menu contextuel des objets blob sélectionnés, puis sélectionnez **Enregistrer sous**. Quand vous enregistrez un objet blob de cette manière, le fichier blob n’est pas ouvert, et le fichier local est créé avec des attributs en lecture/écriture.

### <a name="to-upload-blobs"></a>Pour charger des objets blob

Pour charger des objets blob, sélectionnez le bouton **Charger l’objet blob** quand le conteneur est ouvert sur la vue du conteneur d’objets blob.

Vous pouvez choisir un ou plusieurs fichiers à charger, et vous pouvez charger des fichiers de tout type. La fenêtre **Journal d’activité Azure** affiche la progression du chargement. Pour plus d’informations sur l’utilisation des données d’objets blob, consultez [Utilisation du stockage d’objets blob Azure dans .NET](/azure/storage/blobs/storage-quickstart-blobs-dotnet).

### <a name="to-view-logs-transferred-to-blobs"></a>Pour afficher les journaux d’activité transférés vers des objets blob

Si vous utilisez les diagnostics Azure pour enregistrer des données à partir de votre application Azure et si vous avez transféré des journaux d’activité vers votre compte de stockage, vous verrez les conteneurs qu’Azure a créés pour ces journaux d’activité. L’affichage de ces journaux d’activité dans l’Explorateur de serveurs permet d’identifier facilement les problèmes de votre application, en particulier si elle est déployée sur Azure.

Pour plus d’informations sur les diagnostics Azure, consultez [Collecte des données de journalisation avec les diagnostics Azure](/azure/cloud-services/cloud-services-dotnet-diagnostics).

### <a name="to-get-the-url-for-a-blob"></a>Pour obtenir l’URL d’un objet blob

Ouvrez le menu contextuel de l’objet blob, puis sélectionnez **Copier l’URL**.

### <a name="to-edit-a-blob"></a>Pour modifier un objet blob

Choisissez l’objet BLOB, puis sélectionnez le bouton **ouvrir l’objet BLOB** .

Le fichier est téléchargé vers un emplacement temporaire et ouvert sur l’ordinateur local. Chargez de nouveau l’objet blob chaque fois que vous y apportez des modifications.

## <a name="work-with-queue-resources"></a>Utiliser des ressources de file d’attente

Les files d’attente des services de stockage sont hébergées dans un compte de stockage Azure. Vous pouvez les utiliser pour permettre à vos rôles de service cloud de communiquer entre eux et avec d’autres services par un mécanisme de transmission de messages. Vous pouvez accéder par programmation à la file d’attente via un service cloud et via un service web pour les clients externes. Vous pouvez également accéder à la file d’attente directement à l’aide de l’Explorateur de serveurs dans Visual Studio.

Quand vous développez un service cloud qui utilise des files d’attente, vous pouvez utiliser Visual Studio pour créer des files d’attente et les utiliser de manière interactive quand vous développez et testez votre code.

Dans l’Explorateur de serveurs, vous pouvez afficher les files d’attente dans un compte de stockage, créer et supprimer des files d’attente, ouvrir une file d’attente pour consulter ses messages et ajouter des messages à une file d’attente. Quand vous ouvrez une file d’attente, vous pouvez afficher les messages qu’elle contient. De plus, vous pouvez effectuer les actions suivantes sur la file d’attente à l’aide des boutons situés dans l’angle supérieur gauche :

* Actualiser la vue de la file d’attente.
* Ajoutez un message dans la file d’attente.
* Supprimer le premier message de la file d’attente
* Effacer l’intégralité du contenu de la file d’attente.

L’illustration suivante montre une file d’attente contenant deux messages :

![Affichage d’une file d’attente](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC651470.png)

Pour plus d’informations sur les files d’attente de services de stockage, consultez [Prise en main du stockage de files d’attente Azure à l’aide de .NET](/azure/storage/queues/storage-dotnet-how-to-use-queues). Pour plus d’informations sur le service web des files d’attente des services de stockage, consultez [Concepts de File d’attente](/rest/api/storageservices/Queue-Service-Concepts). Pour plus d’informations sur la façon d’envoyer des messages vers une file d’attente des services de stockage à l’aide de Visual Studio, consultez [Envoi de messages à une file d’attente de services de stockage](/azure/visual-studio/vs-storage-cloud-services-getting-started-queues).

> [!NOTE]
> Les files d’attente de services de stockage sont différentes des files d’attente Azure Service Bus. Pour plus d’informations sur les files d’attente de Service Bus, consultez [service bus files d’attente, rubriques et abonnements](/azure/service-bus-messaging/service-bus-queues-topics-subscriptions).

## <a name="work-with-table-resources"></a>Utiliser des ressources de table

Le stockage de table Azure permet de stocker de grandes quantités de données structurées. Il s'agit d'une banque de données NoSQL qui accepte les appels authentifiés provenant de l'intérieur et de l'extérieur du cloud Azure. Les tables Azure sont idéales pour le stockage des données structurées non relationnelles.

### <a name="to-create-a-table"></a>Pour créer une table

1. Dans **Cloud Explorer**, sélectionnez le nœud **tables** du compte de stockage, puis sélectionnez **créer une table**.
1. Dans la boîte de dialogue **Créer une table** , entrez un nom pour la table.

### <a name="to-view-table-data"></a>Pour afficher des données de table

1. Dans **Cloud Explorer**, ouvrez le nœud **Azure** , puis ouvrez le nœud de **stockage** .
1. Ouvrez le nœud du compte de stockage qui vous intéresse, puis ouvrez le nœud **Tables** pour afficher la liste des tables associées au compte de stockage.
1. Ouvrez le menu contextuel d’une table, puis sélectionnez **Afficher la table**.

    ![Table Azure dans l’Explorateur de solutions](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC744165.png)

La table est organisée en entités (lignes) et propriétés (colonnes). Par exemple, l’illustration suivante montre les entités répertoriées dans le Concepteur de tables.

### <a name="to-edit-table-data"></a>Pour modifier des données de table

Dans **Concepteur de tables**, ouvrez le menu contextuel d’une entité (une seule ligne) ou une propriété (une seule cellule), puis sélectionnez **modifier**.

![Ajouter ou modifier une entité de table](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC656238.png)

Il n’est pas nécessaire que les entités d’une table possèdent les mêmes propriétés (colonnes). Gardez à l’esprit les restrictions suivantes au moment de l’affichage et de la modification des données :

* Vous ne pouvez pas afficher ni modifier des données binaires (`type byte[]`), mais vous pouvez les stocker dans une table.
* Vous ne pouvez pas modifier les valeurs **PartitionKey** ou **RowKey** , car le stockage table Azure ne prend pas en charge cette opération.
* Vous ne pouvez pas créer de propriété appelée **Timestamp**. Les services de stockage Azure utilisent une propriété portant ce nom.
* Si vous entrez une valeur **DateTime** , vous devez respecter un format approprié pour les paramètres régionaux et linguistiques de votre ordinateur (par exemple, mm/jj/aaaa hh : mm : SS [AM | PM] pour l’anglais des États-Unis).

### <a name="to-add-entities"></a>Pour ajouter des entités

1. Dans **Concepteur de tables**, cliquez sur le bouton **Ajouter une entité** .

    ![Bouton Ajouter une entité](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC655336.png)

1. Dans la boîte de dialogue **Ajouter une entité**, saisissez les valeurs des propriétés **PartitionKey** et **RowKey**.

    ![Boîte de dialogue Ajouter une entité](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC655335.png)

    Entrez les valeurs avec précaution. Vous ne pourrez pas les changer après avoir fermé la boîte de dialogue, sauf si vous supprimez l’entité, puis la rajoutez.

### <a name="to-filter-entities"></a>Pour filtrer des entités

Vous pouvez personnaliser les entités qui s’affichent dans une table à l’aide du Générateur de requêtes.

1. Pour ouvrir le Générateur de requêtes, ouvrez une table pour afficher son contenu.
1. Sélectionnez le bouton **Générateur de requêtes** de la vue de la table.

    La boîte de dialogue **Générateur de requêtes** apparaît. L’illustration suivante montre la génération d’une requête dans le Générateur de requêtes.

    ![Générateur de requêtes](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC652231.png)
1. Quand vous avez terminé la création de la requête, fermez la boîte de dialogue. Le formulaire de texte de la requête qui en résulte s’affiche dans une zone de texte en tant que filtre WCF Data Services.
1. Pour exécuter la requête, sélectionnez l’icône représentant un triangle vert.

Vous pouvez également filtrer les données d’entité qui s’affichent dans le Concepteur de tables si vous entrez une chaîne de filtrage WCF Data Services directement dans la zone de texte de filtre. Ce type de chaîne est similaire à une clause SQL WHERE, mais il est toutefois envoyé au serveur en tant que requête HTTP. Pour plus d’informations sur la construction de chaînes de filtre, consultez [construction de chaînes de filtrage pour le concepteur de tables](vs-azure-tools-table-designer-construct-filter-strings.md).

L’illustration suivante montre un exemple de chaîne de filtrage valide :

![Chaîne de filtrage](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC655337.png)

## <a name="refresh-storage-data"></a>Actualiser les données de stockage

Les opérations de connexion aux données et de récupération des données entre l’Explorateur de serveurs et le compte de stockage peuvent prendre jusqu’à une minute. Si Explorateur de serveurs ne peut pas se connecter, l’opération peut expirer. Pendant que les données sont récupérées, vous pouvez continuer à travailler dans d’autres parties de Visual Studio. Pour annuler une opération si elle prend trop de temps, sélectionnez le bouton **Arrêter l’actualisation** dans la barre d’outils de l’Explorateur de serveurs.

### <a name="to-refresh-blob-container-data"></a>Pour actualiser les données d’un conteneur d’objets blob

* Sélectionnez le nœud **Objets blob** sous **Storage**, puis sélectionnez le bouton **Actualiser** dans la barre d’outils de l’Explorateur de serveurs.
* Pour actualiser la liste des objets blob, sélectionnez le bouton **Exécuter**.

### <a name="to-refresh-table-data"></a>Pour actualiser les données d’une table

* Sélectionnez le nœud **Tables** sous **Storage**, puis sélectionnez le bouton **Actualiser** dans la barre d’outils de l’Explorateur de serveurs.
* Pour actualiser la liste des entités affichées dans **Concepteur de tables**, sélectionnez le bouton **exécuter** dans Concepteur de tables.

### <a name="to-refresh-queue-data"></a>Pour actualiser les données d’une file d’attente

Sélectionnez le nœud **Files d’attente** sous **Storage**, puis sélectionnez le bouton **Actualiser** dans la barre d’outils de l’Explorateur de serveurs.

### <a name="to-refresh-all-items-in-a-storage-account"></a>Pour actualiser tous les éléments d’un compte de stockage

Choisissez le nom du compte, puis sélectionnez le bouton **Actualiser** dans la barre d’outils de l’Explorateur de serveurs.

## <a name="add-storage-accounts-by-using-server-explorer"></a>Ajouter des comptes de stockage à l’aide de l’Explorateur de serveurs

Il existe deux façons d’ajouter des comptes de stockage à l’aide de l’Explorateur de serveurs. Vous pouvez créer un compte de stockage dans votre abonnement Azure, ou vous pouvez attacher un compte de stockage existant.

### <a name="to-create-a-storage-account-by-using-server-explorer"></a>Pour créer un compte de stockage à l’aide de l’Explorateur de serveurs

1. Dans l’Explorateur de serveurs, ouvrez le menu contextuel du nœud **Stockage**, puis sélectionnez **Créer un compte de stockage**.

1. Dans la boîte de dialogue **Créer un compte de stockage**, sélectionnez ou entrez les informations suivantes :

   * L’abonnement Azure auquel vous voulez ajouter le compte de stockage
   * Le nom que vous voulez utiliser pour le nouveau compte de stockage
   * La région ou le groupe d’affinités (comme USA Ouest ou Asie Est)
   * Le type de réplication que vous voulez utiliser pour le compte de stockage, par exemple localement redondant

   ![Créer un compte de stockage Azure](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC744166.png)

1. Sélectionnez **Create** (Créer).

Le nouveau compte de stockage s’affiche dans la liste **Stockage** de l’Explorateur de solutions.

### <a name="to-attach-an-existing-storage-account-by-using-server-explorer"></a>Pour attacher un compte de stockage existant à l’aide de l’Explorateur de serveurs

1. Dans l’Explorateur de serveurs, ouvrez le menu contextuel du nœud Azure **Stockage**, puis sélectionnez **Attacher un stockage externe**.

    ![Ajout d’un compte de stockage existant](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC766039.png)
1. Dans la boîte de dialogue **Créer un compte de stockage**, sélectionnez ou entrez les informations suivantes :

   * Le nom du compte de stockage existant que vous voulez attacher.
   * La clé du compte de stockage sélectionné. Cette valeur est généralement fournie quand vous sélectionnez un compte de stockage. Si vous voulez que Visual Studio se souvienne de la clé du compte de stockage, cochez la case **Mémoriser la clé du compte**.
   * Le protocole à utiliser pour se connecter au compte de stockage, par exemple HTTP, HTTPS ou un point de terminaison personnalisé. Pour plus d’informations sur les points de terminaison personnalisés, consultez [Configuration de chaînes de connexion](/azure/storage/common/storage-configure-connection-string).

### <a name="to-view-the-secondary-endpoints"></a>Pour afficher les points de terminaison secondaires

Si vous avez créé un compte de stockage à l’aide de l’option de réplication **Read-Access Geo Redundant**, vous pouvez afficher ses points de terminaison secondaires en ouvrant le menu contextuel du nom du compte, puis en sélectionnant **Propriétés**.

![Points de terminaison de stockage secondaires](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC766040.png)

### <a name="to-remove-a-storage-account-from-server-explorer"></a>Pour supprimer un compte de stockage depuis l’Explorateur de serveurs

Dans l’Explorateur de serveurs, ouvrez le menu contextuel du compte, puis sélectionnez **Supprimer**.

Si vous supprimez un compte de stockage, toutes les informations de clé enregistrées pour ce compte seront également supprimées.

Si vous supprimez un compte de stockage à partir de l’Explorateur de serveurs, cela n’affecte pas votre compte de stockage ni les données qu’il contient. Cela supprime simplement sa référence dans l’Explorateur de serveurs. Pour supprimer définitivement un compte de stockage, utilisez le [portail Azure](https://portal.azure.com/).

## <a name="next-steps"></a>Étapes suivantes

Pour en savoir plus sur l’utilisation des services de stockage Azure, consultez la page [Accès aux services de stockage Azure](/azure/storage/common/storage-introduction).
