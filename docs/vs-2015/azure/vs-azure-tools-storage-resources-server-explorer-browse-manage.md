---
title: Parcourir et gérer des ressources de stockage à l’aide de l’Explorateur de serveurs | Microsoft Docs
description: Consultation et gestion des ressources de stockage à l’aide de l’Explorateur de serveurs
author: ghogen
manager: douge
assetId: 658dc064-4a4e-414b-ae5a-a977a34c930d
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 8/24/2017
ms.author: ghogen
ms.openlocfilehash: 00229cd88ddcab4d2d59ae40202620c374415e4b
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2018
ms.locfileid: "51002072"
---
# <a name="browse-and-manage-storage-resources-by-using-server-explorer"></a>Parcourir et gérer des ressources de stockage avec l’Explorateur de serveurs

[!INCLUDE [storage-try-azure-tools](./includes/storage-try-azure-tools.md)]

## <a name="overview"></a>Vue d'ensemble

Si vous avez installé Azure Tools pour Microsoft Visual Studio, vous pouvez afficher des objets blob, file d’attente et les données de table à partir de vos comptes de stockage pour Azure. Azure **stockage** nœud dans l’Explorateur de serveurs affiche les données qui se trouve dans votre compte d’émulateur de stockage local et vos autres comptes de stockage Azure.

Pour afficher l’Explorateur de serveurs dans Visual Studio, dans la barre de menus, sélectionnez **vue** > **Explorateur de serveurs**. Le **stockage** nœud affiche tous les comptes de stockage qui existent sous chaque abonnement Azure ou le certificat que vous êtes connecté. Si votre compte de stockage n’apparaît pas, vous pouvez l’ajouter en suivant les instructions [plus loin dans cet article](#add-storage-accounts-by-using-server-explorer).

À partir de Azure SDK 2.7, vous pouvez également utiliser Cloud Explorer pour afficher et gérer vos ressources Azure. Pour plus d’informations, consultez [gestion des ressources Azure avec Cloud Explorer](vs-azure-tools-resources-managing-with-cloud-explorer.md).

## <a name="view-and-manage-storage-resources-in-visual-studio"></a>Afficher et gérer les ressources de stockage dans Visual Studio

Explorateur de serveurs affiche automatiquement une liste d’objets BLOB, files d’attente et tables dans votre compte d’émulateur de stockage. Le compte de l’émulateur de stockage est répertorié dans l’Explorateur de serveurs sous le **stockage** nœud en tant que le **développement** nœud.

Pour afficher les ressources du compte de l’émulateur de stockage, développez le **développement** nœud. Si l’émulateur de stockage n’a pas été démarré quand vous développez le **développement** nœud, il démarre automatiquement. Ce processus peut prendre plusieurs secondes. Vous pouvez continuer à travailler dans d’autres zones de Visual Studio pendant le démarrage de l’émulateur de stockage.

Pour afficher les ressources dans un compte de stockage, développez le nœud du compte de stockage dans l’Explorateur de serveurs où vous voyez **Blobs**, **files d’attente**, et **Tables** nœuds.

## <a name="work-with-blob-resources"></a>Utiliser des ressources de l’objet blob

Le **Blobs** nœud affiche une liste de conteneurs pour le compte de stockage sélectionné. Conteneurs d’objets BLOB contiennent des fichiers d’objets blob, et vous pouvez organiser ces objets BLOB dans les dossiers et sous-dossiers. Pour plus d’informations, consultez [comment utiliser le stockage d’objets Blob à partir de .NET](/azure/storage/blobs/storage-dotnet-how-to-use-blobs).

### <a name="to-create-a-blob-container"></a>Pour créer un conteneur d’objets blob

1. Ouvrez le menu contextuel pour le **Blobs** nœud, puis sélectionnez **créer un conteneur d’objets Blob**.
1. Dans le **créer un conteneur d’objets Blob** boîte de dialogue, entrez le nom du nouveau conteneur.  
1. Sélectionnez entrée sur votre clavier, ou vous pouvez cliquez ou appuyez en dehors du champ de nom pour enregistrer le conteneur d’objets blob.

   > [!NOTE]
   > Le nom de conteneur d’objets blob doit commencer par un chiffre (0-9) ou d’une lettre minuscule (a-z).

### <a name="to-delete-a-blob-container"></a>Pour supprimer un conteneur d’objets blob

Ouvrez le menu contextuel pour le conteneur d’objets blob que vous souhaitez supprimer, puis sélectionnez **supprimer**.

### <a name="to-display-a-list-of-the-items-in-a-blob-container"></a>Pour afficher la liste des éléments dans un conteneur d’objets blob

Ouvrez le menu contextuel d’un conteneur d’objets blob dans la liste, puis sélectionnez **Open**.

Lorsque vous affichez le contenu d’un conteneur d’objets blob, il apparaît sur un onglet appelé à la vue du conteneur d’objets blob.

![Vue du conteneur d’objets BLOB](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC749016.png)

Vous pouvez effectuer les opérations suivantes sur les objets BLOB dans le coin supérieur droit de la vue du conteneur d’objets blob à l’aide des boutons :

* Entrez une valeur de filtre et l’appliquer.
* Actualiser la liste des objets BLOB du conteneur.
* Téléchargez un fichier.
* Supprimer un objet blob. (Suppression d’un fichier à partir d’un conteneur d’objets blob ne supprime pas le fichier sous-jacent. Il est uniquement supprimé du conteneur d’objets blob.)
* Ouvrir un objet blob.
* Enregistrer un objet blob à l’ordinateur local.

### <a name="to-create-a-folder-or-subfolder-in-a-blob-container"></a>Pour créer un dossier ou sous-dossier dans un conteneur d’objets blob

1. Choisissez le conteneur d’objets blob dans Cloud Explorer. Dans la fenêtre du conteneur, sélectionnez le **charger l’objet Blob** bouton.

1. Dans le **télécharger un nouveau fichier** boîte de dialogue, sélectionnez le **Parcourir** pour spécifier le fichier que vous souhaitez télécharger, puis entrez un nom de dossier dans le **dossier (facultatif)** boîte.

   ![Téléchargement d’un fichier dans un dossier d’objets blob](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC766037.png)

   Vous pouvez ajouter des sous-dossiers dans les dossiers du conteneur en suivant la même étape. Si vous ne spécifiez pas un nom de dossier, le fichier est téléchargé vers le niveau supérieur du conteneur d’objets blob. Le fichier apparaît dans le dossier spécifié dans le conteneur.

   ![Dossier ajouté à un conteneur d’objets blob](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC766038.png)

1. Double-cliquez sur le dossier ou appuyez sur ENTRÉE pour afficher le contenu du dossier. Lorsque vous êtes dans le dossier, vous pouvez revenir à la racine du conteneur en sélectionnant le **ouvrir le répertoire Parent** (flèche).

### <a name="to-delete-a-container-folder"></a>Pour supprimer un dossier conteneur

Supprimer tous les fichiers dans le dossier.

Dossiers des conteneurs d’objets blob sont des dossiers virtuels, vous ne pouvez pas créer un dossier vide. Vous ne pouvez pas supprimer un dossier pour supprimer son contenu, mais vous devez supprimer tout le contenu d’un dossier à supprimer le dossier lui-même.

### <a name="to-filter-blobs-in-a-container"></a>Pour filtrer les objets BLOB dans un conteneur

Vous pouvez filtrer les objets BLOB qui sont affichés en spécifiant un préfixe commun.

Par exemple, si vous entrez le préfixe **hello** dans la zone de texte de filtre, puis sélectionnez le **Execute** (**!**) bouton, seuls les objets BLOB qui commencent par « hello » s’affiche pas.

![Zone de texte de filtre](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC519076.png)

La zone de texte de filtre respecte la casse et ne prend en charge le filtrage avec des caractères génériques. Objets BLOB peut être filtrés que par préfixe. Le préfixe peut inclure un délimiteur si vous utilisez des délimiteurs pour organiser les objets BLOB en hiérarchie virtuelle. Par exemple, un filtrage sur le préfixe « HelloFabric / » retourne tous les objets BLOB qui commencent par cette chaîne.

### <a name="to-download-blob-data"></a>Pour télécharger les données d’objets blob

Dans Cloud Explorer, utilisez une des méthodes suivantes :

* Ouvrez le menu contextuel pour un ou plusieurs objets BLOB, puis sélectionnez **Open**.
* Sélectionnez le nom d’objet blob, puis le **Open** bouton.
* Double-cliquez sur le nom d’objet blob.

La progression d’un téléchargement de l’objet blob s’affiche dans le **journal d’activité Azure** fenêtre.

L’objet blob s’ouvre dans l’éditeur par défaut pour ce type de fichier. Si le système d’exploitation reconnaît le type de fichier, le fichier s’ouvre dans une application installée localement. Sinon, vous êtes invité à choisir une application qui est appropriée pour le type de fichier de l’objet blob. Le fichier local qui est créé lorsque vous téléchargez un objet blob est marqué comme étant en lecture seule.

Données d’objet BLOB sont mis en cache localement et vérifiées par rapport à l’heure de dernière modification de l’objet blob dans stockage Blob Azure. Si l’objet blob a été mis à jour depuis son dernier téléchargement, il est à nouveau téléchargé. Sinon, l’objet blob est chargé à partir du disque local.

Par défaut, un objet blob est téléchargé dans un répertoire temporaire. Pour télécharger des objets BLOB dans un répertoire spécifique, ouvrez le menu contextuel pour les noms d’objets blob sélectionnés et sélectionnez **Enregistrer sous**. Lorsque vous enregistrez un objet blob de cette manière, le fichier blob n’est pas ouvert, et le fichier local est créé avec les attributs de lecture/écriture.

### <a name="to-upload-blobs"></a>Pour charger des objets BLOB

Pour charger des objets BLOB, sélectionnez le **charger l’objet Blob** bouton lorsque le conteneur est ouvert sur la vue du conteneur d’objets blob.

Vous pouvez choisir un ou plusieurs fichiers à charger, et vous pouvez télécharger des fichiers de n’importe quel type. Le **journal d’activité Azure** fenêtre affiche la progression du téléchargement. Pour plus d’informations sur l’utilisation des données d’objets blob, consultez [comment utiliser le stockage Blob Azure dans .NET](http://go.microsoft.com/fwlink/p/?LinkId=267911).

### <a name="to-view-logs-transferred-to-blobs"></a>Pour afficher les journaux transférés vers des objets BLOB

Si vous utilisez les Diagnostics de Azure pour enregistrer des données à partir de votre application Windows Azure et que vous avez transféré des journaux à votre compte de stockage, vous verrez les conteneurs qu’Azure a créée pour ces journaux. Affichage de ces journaux dans l’Explorateur de serveurs d’est un moyen facile d’identifier des problèmes avec votre application, en particulier si elle est déployée sur Azure.

Pour plus d’informations sur les Diagnostics Azure, consultez [collecter des données de journaux à l’aide des Diagnostics Azure](https://msdn.microsoft.com/library/azure/gg433048.aspx).

### <a name="to-get-the-url-for-a-blob"></a>Pour obtenir l’URL d’un objet blob

Ouvrez le menu contextuel de l’objet blob et sélectionnez **copier l’URL**.

### <a name="to-edit-a-blob"></a>Pour modifier un objet blob

Sélectionnez l’objet blob, puis le **ouvrir l’objet Blob** bouton.

Le fichier est téléchargé vers un emplacement temporaire et ouvert sur l’ordinateur local. Charger à nouveau l’objet blob une fois que vous apportez des modifications.

## <a name="work-with-queue-resources"></a>Travailler avec des ressources de file d’attente

Files d’attente de services de stockage sont hébergées dans un compte de stockage Azure. Vous pouvez les utiliser pour permettre à votre cloud des rôles de service communiquer entre eux et avec d’autres services par un mécanisme de transmission de messages. Vous pouvez accéder par programmation la file d’attente via un service cloud et via un service web pour les clients externes. Vous pouvez également accéder à la file d’attente directement à l’aide de l’Explorateur de serveurs dans Visual Studio.

Lorsque vous développez un service cloud qui utilise des files d’attente, vous souhaiterez peut-être utiliser Visual Studio pour créer des files d’attente et d’utiliser de manière interactive pendant que vous développez et testez votre code.

Dans l’Explorateur de serveurs, vous pouvez afficher les files d’attente dans un compte de stockage, créer et supprimer des files d’attente, ouvrir une file d’attente pour consulter ses messages et ajouter des messages à une file d’attente. Lorsque vous ouvrez une file d’attente pour l’affichage, vous pouvez afficher les messages individuels, et vous pouvez effectuer les actions suivantes sur la file d’attente à l’aide des boutons dans le coin supérieur gauche :

* Actualisez l’affichage de la file d’attente.
* Ajouter un message à la file d’attente.
* La file d’attente le premier message.
* Effacer la file d’attente entière.

L’illustration suivante montre une file d’attente contenant deux messages :

![Affichage d’une file d’attente](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC651470.png)

Pour plus d’informations sur le stockage de files d’attente des services, consultez [prise en main Azure Queue storage à l’aide de .NET](http://go.microsoft.com/fwlink/?LinkID=264702). Pour plus d’informations sur le service web pour les services de stockage de files d’attente, consultez [Concepts de Service de file d’attente](http://go.microsoft.com/fwlink/?LinkId=264788). Pour plus d’informations sur la façon d’envoyer des messages à une file d’attente des services de stockage à l’aide de Visual Studio, consultez [envoi de Messages à une file d’attente des Services de stockage](https://docs.microsoft.com/azure/visual-studio/vs-storage-cloud-services-getting-started-queues).

> [!NOTE]
> Files d’attente de services de stockage sont différentes des files d’attente Azure Service Bus. Pour plus d’informations sur les files d’attente Service Bus, consultez [files d’attente Service Bus, rubriques et abonnements](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-queues-topics-subscriptions).

## <a name="work-with-table-resources"></a>Travailler avec des ressources de table

Stockage Table Azure stocke de grandes quantités de données structurées. Le service est une banque de données NoSQL qui accepte des appels authentifiés provenant de l’intérieur et extérieur du cloud Azure. Les tables Azure sont adaptés au stockage des données non relationnelles structurées.

### <a name="to-create-a-table"></a>Pour créer une table

1. Dans Cloud Explorer, sélectionnez le **Tables** nœud de compte de stockage, puis sélectionnez **Create Table**.
1. Dans le **Create Table** boîte de dialogue, entrez un nom pour la table.

### <a name="to-view-table-data"></a>Pour afficher les données de table

1. Dans Cloud Explorer, ouvrez le **Azure** nœud, puis ouvrez le **stockage** nœud.
1. Ouvrez le nœud de compte de stockage qui vous intéresse, puis ouvrez le **Tables** nœud pour afficher la liste des tables pour le compte de stockage.
1. Ouvrez le menu contextuel pour une table, puis sélectionnez **vue Table**.

    ![Une table Azure dans l’Explorateur de solutions](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC744165.png)

La table est organisée en entités (lignes) et des propriétés (colonnes). Par exemple, l’illustration suivante montre les entités répertoriées dans le Concepteur de tables.

### <a name="to-edit-table-data"></a>Pour modifier les données de table

Dans le Concepteur de tables, ouvrez le menu contextuel pour une entité (une seule ligne) ou une propriété (une seule cellule), puis sélectionnez **modifier**.

    ![Add or edit a table entity](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC656238.png)

Entités dans une seule table ne sont pas doit posséder le même ensemble de propriétés (colonnes). Gardez à l’esprit les restrictions suivantes sur l’affichage et modification des données :

* Vous ne pouvez pas afficher ou modifier des données binaires (`type byte[]`), mais vous pouvez les stocker dans une table.
* Vous ne pouvez pas modifier le **PartitionKey** ou **RowKey** valeurs, étant donné que le stockage de Table dans Azure ne prend pas en charge cette opération.
* Vous ne pouvez pas créer une propriété appelée **Timestamp**. Services de stockage Azure utilisent une propriété portant ce nom.
* Si vous entrez un **DateTime** valeur, vous devez respecter un format approprié pour les paramètres linguistiques et régionaux de votre ordinateur (par exemple, MM/jj/aaaa hh [AM | PM] pour l’anglais américain).

### <a name="to-add-entities"></a>Pour ajouter des entités

1. Dans le Concepteur de tables, sélectionnez le **ajouter une entité** bouton.

    ![Bouton Ajouter une entité](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC655336.png)

1. Dans le **ajouter une entité** boîte de dialogue, entrez les valeurs de la **PartitionKey** et **RowKey** propriétés.

    ![Ajouter la boîte de dialogue d’entité](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC655335.png)

    Entrez les valeurs avec précaution. Vous ne pouvez pas les modifier après avoir fermé la boîte de dialogue, sauf si vous supprimez l’entité et l’ajouter à nouveau.

### <a name="to-filter-entities"></a>Pour filtrer des entités

Vous pouvez personnaliser le jeu d’entités qui apparaissent dans une table si vous utilisez le Générateur de requêtes.

1. Pour ouvrir le Générateur de requêtes, ouvrez une table pour l’affichage.
1. Sélectionnez le **Générateur de requêtes** bouton de barre d’outils de la vue de la table.

    Le **Générateur de requêtes** boîte de dialogue s’affiche. L’illustration suivante montre une requête qui est en cours de génération dans le Générateur de requêtes.

    ![Générateur de requêtes](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC652231.png)
1. Lorsque vous avez terminé la création de la requête, fermez la boîte de dialogue. Le formulaire de texte résultant de la requête s’affiche dans une zone de texte comme un filtre de WCF Data Services.
1. Pour exécuter la requête, sélectionnez l’icône de triangle vert.

Vous pouvez également filtrer les données d’entité qui s’affiche dans le Concepteur de tables si vous entrez une chaîne de filtrage WCF Data Services directement dans la zone de texte de filtre. Ce type de chaîne est similaire à une clause SQL WHERE, mais est envoyé au serveur en tant qu’une requête HTTP. Pour plus d’informations sur la façon de construire des chaînes de filtre, consultez [Constructing des chaînes de filtrage pour le Concepteur de tables](https://docs.microsoft.com/azure/vs-azure-tools-table-designer-construct-filter-strings).

L’illustration suivante montre un exemple de chaîne de filtrage valides :

![Chaîne de filtrage](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC655337.png)

## <a name="refresh-storage-data"></a>Actualiser les données de stockage

Lors de l’Explorateur de serveurs se connecte à ou obtient des données à partir d’un compte de stockage, l’opération peut prendre une minute pour terminer. Si l’Explorateur de serveurs ne peut pas se connecter, l’opération peut expirer. Alors que les données sont récupérées, vous pouvez continuer à travailler dans d’autres parties de Visual Studio. Pour annuler l’opération si elle est trop longue, sélectionnez le **arrêter l’actualisation** dans la barre d’outils de l’Explorateur de serveurs.

### <a name="to-refresh-blob-container-data"></a>Pour actualiser les données de conteneur d’objets blob

* Sélectionnez le **Blobs** nœud sous **stockage**, puis sélectionnez le **Actualiser** dans la barre d’outils de l’Explorateur de serveurs.
* Pour actualiser la liste d’objets BLOB qui s’affiche, sélectionnez le **Execute** bouton.

### <a name="to-refresh-table-data"></a>Pour actualiser les données de table

* Sélectionnez le **Tables** nœud sous **stockage**, puis sélectionnez le **Actualiser** dans la barre d’outils de l’Explorateur de serveurs.
* Pour actualiser la liste des entités qui s’affiche dans le Concepteur de tables, sélectionnez le **Execute** bouton dans le Concepteur de tables.

### <a name="to-refresh-queue-data"></a>Pour actualiser les données de la file d’attente

Sélectionnez le **files d’attente** nœud sous **stockage**, puis sélectionnez le **Actualiser** dans la barre d’outils de l’Explorateur de serveurs.

### <a name="to-refresh-all-items-in-a-storage-account"></a>Pour actualiser tous les éléments dans un compte de stockage

Choisissez le nom du compte, puis sélectionnez le **Actualiser** dans la barre d’outils de l’Explorateur de serveurs.

## <a name="add-storage-accounts-by-using-server-explorer"></a>Ajouter des comptes de stockage à l’aide de l’Explorateur de serveurs

Il existe deux façons d’ajouter des comptes de stockage à l’aide de l’Explorateur de serveurs. Vous pouvez créer un compte de stockage dans votre abonnement Azure, ou vous pouvez attacher un compte de stockage existant.

### <a name="to-create-a-storage-account-by-using-server-explorer"></a>Pour créer un compte de stockage à l’aide de l’Explorateur de serveurs

1. Dans l’Explorateur de serveurs, ouvrez le menu contextuel pour le **stockage** nœud, puis sélectionnez **créer un compte de stockage**.

1. Dans le **créer un compte de stockage** boîte de dialogue zone, sélectionnez ou entrez les informations suivantes :

   * L’abonnement Azure auquel vous souhaitez ajouter le compte de stockage.
   * Le nom que vous souhaitez utiliser pour le nouveau compte de stockage.
   * La région ou le groupe d’affinités (par exemple, ouest des États-Unis ou Asie).
   * Le type de réplication que vous souhaitez utiliser pour le compte de stockage, par exemple localement redondant.

   ![Créer un compte de stockage Azure](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC744166.png)

1. Sélectionnez **Créer**.

Le nouveau compte de stockage apparaît dans le **stockage** liste dans l’Explorateur de solutions.

### <a name="to-attach-an-existing-storage-account-by-using-server-explorer"></a>Pour attacher un compte de stockage existant à l’aide de l’Explorateur de serveurs

1. Dans l’Explorateur de serveurs, ouvrez le menu contextuel pour le Azure **stockage** nœud, puis sélectionnez **attacher un stockage externe**.

    ![Ajout d’un compte de stockage existant](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC766039.png)
1. Dans le **créer un compte de stockage** boîte de dialogue zone, sélectionnez ou entrez les informations suivantes :

   * Le nom du compte de stockage existant que vous voulez attacher.
   * La clé du compte de stockage sélectionné. Cette valeur est généralement fournie pour vous lorsque vous sélectionnez un compte de stockage. Si vous souhaitez que Visual Studio se souvienne de la clé de compte de stockage, sélectionnez le **clé du compte de mémoriser** case à cocher.
   * Le protocole à utiliser pour se connecter au compte de stockage, tels que HTTP, HTTPS ou un point de terminaison personnalisé. Pour plus d’informations sur les points de terminaison personnalisés, consultez [comment configurer les chaînes de connexion](https://msdn.microsoft.com/library/azure/ee758697.aspx).

### <a name="to-view-the-secondary-endpoints"></a>Pour afficher les points de terminaison secondaire

Si vous avez créé un compte de stockage à l’aide de la **Read-Access Geo Redundant** option de réplication, vous pouvez afficher ses points de terminaison secondaire en ouvrant le menu contextuel pour le nom du compte, puis sélectionnez **propriétés**.

![Points de terminaison de stockage secondaire](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC766040.png)

### <a name="to-remove-a-storage-account-from-server-explorer"></a>Pour supprimer un compte de stockage à partir de l’Explorateur de serveurs

Dans l’Explorateur de serveurs, ouvrez le menu contextuel pour le nom du compte, puis sélectionnez **supprimer**. 

Si vous supprimez un compte de stockage, les informations de clé enregistrées pour ce compte sont également supprimées.

Si vous supprimez un compte de stockage à partir de l’Explorateur de serveurs, il n’affecte pas votre compte de stockage ni les données qu’il contient. Il supprime simplement la référence de l’Explorateur de serveurs. Pour supprimer définitivement un compte de stockage, utilisez le [Azure portal](https://portal.azure.com/).

## <a name="next-steps"></a>Étapes suivantes

Pour en savoir plus sur l’utilisation des services de stockage Azure, consultez [l’accès aux Services de stockage Azure](https://msdn.microsoft.com/library/azure/ee405490.aspx).
