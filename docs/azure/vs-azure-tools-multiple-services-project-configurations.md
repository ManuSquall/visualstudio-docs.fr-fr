---
title: Configurer un projet Azure avec plusieurs configurations de service
description: Découvrez comment configurer un projet de service cloud Azure en modifiant les fichiers ServiceDefinition.csdef, ServiceConfiguration.Local.cscfg et ServiceConfiguration.Cloud.cscfg.
author: ghogen
manager: jillfra
assetId: a4fb79ed-384f-4183-9f74-5cac257206b9
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/11/2017
ms.author: ghogen
ms.openlocfilehash: 7b9df8c5609c92a6b6631d1ed9fdda8d65e9b605
ms.sourcegitcommit: 257fc60eb01fefafa9185fca28727ded81b8bca9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72911807"
---
# <a name="configuring-your-azure-project-in-visual-studio-to-use-multiple-service-configurations"></a>Configuration de votre projet Azure dans Visual Studio pour utiliser plusieurs configurations de service

Un projet de service cloud Azure dans Visual Studio inclut trois fichiers de configuration : `ServiceDefinition.csdef`, `ServiceConfiguration.Local.cscfg` et `ServiceConfiguration.Cloud.cscfg` :

- `ServiceDefinition.csdef` est déployé sur Azure pour décrire les prérequis du service cloud et de ses rôles, et pour fournir les paramètres applicables à toutes les instances. Les paramètres peuvent être lus au moment de l’exécution à l’aide de l’API du runtime d’hébergement du service Azure. Ce fichier peut être mis à jour sur Azure uniquement lorsque le service cloud est arrêté.
- `ServiceConfiguration.Local.cscfg` et `ServiceConfiguration.Cloud.cscfg` fournissent les valeurs des paramètres dans le fichier de définition, et spécifient le nombre d'instances à exécuter pour chaque rôle. Le fichier « Local » contient les valeurs utilisées dans le débogage local ; le fichier « Cloud » est déployé sur Azure en tant que `ServiceConfiguration.cscfg` et fournit les paramètres de l'environnement du serveur. Ce fichier peut être mis à jour lorsque votre service cloud est en cours d’exécution dans Azure.

Les paramètres de configuration sont gérés et modifiés dans Visual Studio à l'aide des pages de propriétés du rôle concerné (cliquez avec le bouton droit sur le rôle, sélectionnez **Propriétés** ou double-cliquez sur le rôle). Les modifications peuvent être étendues à la configuration choisie dans la liste déroulante **Configuration du service**. Les propriétés des rôles web et de travail sont similaires, sauf si elles sont décrites dans les sections suivantes.

![VS_Solution_Explorer_Roles_Properties](./media/vs-azure-tools-multiple-services-project-configurations/IC784076.png)

Pour en savoir plus sur les schémas sous-jacents des fichiers de définition et de configuration de service, consultez les articles relatifs au [schéma XML .csdef](/azure/cloud-services/schema-csdef-file) et au [schéma XML .cscfg](/azure/cloud-services/schema-cscfg-file). Pour plus d'informations sur la configuration de service, consultez [Configuration de Cloud Services](/azure/cloud-services/cloud-services-how-to-configure-portal).

## <a name="configuration-page"></a>Page de configuration

### <a name="service-configuration"></a>Configuration du service

Sélectionne le `ServiceConfiguration.*.cscfg` affecté par les modifications. Par défaut, il existe des variantes Local et Cloud, et vous pouvez utiliser la commande **Gérer...** pour copier, renommer et supprimer des fichiers de configuration. Ces fichiers sont ajoutés à votre projet de service cloud et apparaissent dans l'**Explorateur de solutions**. Cependant, la modification du nom ou la suppression des configurations ne peuvent s'effectuer qu'à l'aide de ce contrôle.

### <a name="instances"></a>Instances

Définir la propriété count de l’ **Instance** au nombre d'instances que le service doit exécuter pour ce rôle.

Définir la propriété **Taille de la machine virtuelle** sur **Très petite**, **Petite**, **Moyenne**, **Grande** ou **Très grande**.  Pour en savoir plus, consultez la rubrique [Tailles de services cloud](/azure/cloud-services/cloud-services-sizes-specs).

### <a name="startup-action-web-role-only"></a>Action de démarrage (rôle web uniquement)

Définissez cette propriété pour spécifier que Visual Studio doit lancer un navigateur web pour les points de terminaison HTTP, les points de terminaison HTTPS, ou les deux lorsque vous commencez le débogage.

L'option **Point de terminaison HTTPS** est disponible uniquement si vous avez déjà défini un point de terminaison HTTPS pour votre rôle. Vous pouvez définir un point de terminaison HTTPS sur la page Propriétés des **Points de terminaison** .

Si vous avez déjà ajouté un point de terminaison HTTPS, l'option point de terminaison HTTPS est activée par défaut et Visual Studio lance un navigateur pour ce point de terminaison lorsque vous démarrez le débogage, ainsi qu'un navigateur pour votre point de terminaison HTTP, à condition d'activer les deux options de démarrage.

### <a name="diagnostics"></a>Diagnostics

Par défaut, les diagnostics sont activés pour le rôle web. Le projet de service cloud Azure et le compte de stockage sont configurés pour utiliser l'émulateur de stockage local. Lorsque vous êtes prêt à déployer sur Azure, vous pouvez sélectionner le bouton de génération ( **...** ) pour utiliser plutôt Stockage Azure. Vous pouvez transférer les données de diagnostic au compte de stockage à la demande ou à intervalles planifiés automatiquement. Pour plus d'informations sur les diagnostics Azure, consultez la page [Activation de Diagnostics dans Azure Cloud Services et Azure Virtual Machines](/azure/cloud-services/cloud-services-dotnet-diagnostics).

## <a name="settings-page"></a>Page Paramètres

Sur la page **Paramètres**, vous pouvez ajouter des paramètres à une configuration sous la forme de paires nom-valeur. Le code qui s’exécute dans le rôle peut lire les valeurs de vos paramètres de configuration au moment de l’exécution à l’aide des classes fournies par la [bibliothèque managée Azure](/previous-versions/azure/dn602775(v=azure.11)), en particulier la méthode [GetConfigurationSettingValue](/previous-versions/azure/reference/ee772857(v=azure.100)) .

### <a name="configuring-a-connection-string-for-a-storage-account"></a>Configuration d’une chaîne de connexion pour un compte de stockage

Une chaîne de connexion est un paramètre de qui fournit des informations de connexion et d'authentification à l'émulateur de stockage ou à un compte de stockage Azure. Chaque fois que le code d'un rôle accède au stockage Azure (objets blob, files d'attente ou tables), il a besoin d'une chaîne de connexion.

> [!Note]
> Une chaîne de connexion pour un compte de stockage Azure doit utiliser un format défini (voir [Configuration des chaînes de connexion Stockage Azure](/azure/storage/common/storage-configure-connection-string)).

Vous pouvez définir la chaîne de connexion pour utiliser un stockage local si nécessaire, puis définir un compte de stockage Azure lorsque vous déployez l'application dans le service cloud. Si vous ne parvenez pas à définir correctement la chaîne de connexion, votre rôle pourrait ne pas démarrer, ou alterner entre les états initialisation, occupé et arrêt.

Pour créer une chaîne de connexion, sélectionnez **Ajouter un paramètre** et définissez **Type** sur « Chaîne de connexion ».

Pour les chaînes de connexion nouvelles ou existantes, sélectionnez **...** * à droite du champ **Valeur** pour ouvrir la boîte de dialogue **Créer une chaîne de connexion de stockage** :

1. Sous **Se connecter en utilisant**, sélectionnez l'option **Votre abonnement** pour sélectionner un compte de stockage à partir d'un abonnement. Visual Studio obtient ensuite automatiquement les informations d'identification du compte de stockage à partir du fichier `.publishsettings`.
1. L'option **Informations d'identification entrées manuellement** vous permet de spécifier directement le nom et la clé du compte à l'aide des informations du portail Azure. Pour copier la clé du compte :
    1. Accédez au compte de stockage sur le portail Azure et sélectionnez **Gérer les clés**.
    1. Pour copier la clé de compte, accédez au compte de stockage sur le portail Azure, sélectionnez **Paramètres > clés d’accès**, puis utilisez le bouton Copier pour copier la clé d’accès primaire dans le Presse-papiers.
1. Sélectionnez l'une des options de connexion. L'option **Spécifier des points de terminaison personnalisés** vous demande de spécifier des URL spécifiques pour les objets blob, les tables et les files d'attente. Les points de terminaison personnalisés vous permettent d'utiliser des [domaines personnalisés](/azure/storage/blobs/storage-custom-domain-name) et de contrôler plus précisément l'accès. Voir [Configuration des chaînes de connexion du Stockage Azure](/azure/storage/common/storage-configure-connection-string).
1. Sélectionnez **OK**, puis **Fichier > Enregistrer** pour mettre à jour la configuration avec la nouvelle chaîne de connexion.

Ici encore, lorsque vous publiez votre application dans Azure, sélectionnez la configuration de service qui contient le compte de stockage Azure pour la chaîne de connexion. Une fois votre application publiée, vérifiez que l'application fonctionne comme prévu par rapport aux services de stockage Azure.

Pour plus d’informations sur la procédure de mise à jour des configurations de service, consultez la section [Gérer les chaînes de connexion pour les comptes de stockage](vs-azure-tools-configure-roles-for-cloud-service.md#manage-connection-strings-for-storage-accounts).

## <a name="endpoints-page"></a>Page des points de terminaison

Un rôle web comporte généralement un seul point de terminaison HTTP sur le port 80. En revanche, un rôle de travail peut avoir un nombre quelconque de points de terminaison HTTP, HTTPS ou TCP. Les points de terminaison peuvent être des points de terminaison d'entrée, accessibles aux clients externes, ou des points de terminaison internes, accessibles aux autres rôles qui s'exécutent dans le service.

- Pour rendre un point de terminaison HTTP accessible aux clients externes et aux navigateurs web, spécifiez « Entrée » comme type de point de terminaison et spécifiez un nom et un numéro de port public.
- Pour rendre un point de terminaison HTTPS accessible aux clients externes et aux navigateurs web, spécifiez **Entrée**comme type de point de terminaison et spécifiez un nom, un numéro de port public et un nom de certificat de gestion. Vous devez également définir le certificat sur la page de propriétés des **certificats** pour pouvoir spécifier un certificat de gestion.
- Pour rendre un point de terminaison accessible en interne par les autres rôles du service cloud, spécifiez « Interne » comme type de point de terminaison et spécifiez un nom et des ports privés potentiels pour ce point de terminaison.

## <a name="local-storage-page"></a>Page de stockage local

Vous pouvez utiliser la page de propriétés du **Stockage local** pour réserver une ou plusieurs ressources de stockage local pour un rôle. Une ressource de stockage local est un répertoire réservé dans le système de fichiers de la machine virtuelle Azure dans lequel s’exécute l’instance d’un rôle.

## <a name="certificates-page"></a>Page Certificats

La page de propriétés **Certificats** ajoute des informations sur vos certificats à votre configuration de service. Notez que vos certificats ne sont pas empaquetés avec votre service. Vous devez les charger séparément sur Azure, via le [portail Azure](https://portal.azure.com).

L'ajout d'un certificat ici ajoute des informations sur vos certificats à votre configuration de service. Les certificats ne sont pas empaquetés avec le service. Vous devez les charger séparément via le portail Azure.

Pour associer un certificat à votre rôle, donnez un nom au certificat. Ce nom permet de faire référence au certificat lorsque vous configurez un point de terminaison HTTPS dans la page **Points de terminaison**. Ensuite, spécifiez si le magasin de certificats est **Machine locale** ou **Utilisateur actuel** et le nom du magasin. Enfin, entrez l'empreinte du certificat. Si le certificat est dans Utilisateur actuel\Mon magasin, vous pouvez entrer l'empreinte du certificat en sélectionnant le certificat à partir d'une liste. S'il se trouve à un autre emplacement, entrez la valeur de l'empreinte numérique à la main.

Lorsque vous ajoutez un certificat à partir du magasin de certificats, les éventuels certificats intermédiaires sont automatiquement ajoutés aux paramètres de configuration. Par ailleurs, ces certificats intermédiaires doivent être chargés sur Azure afin de configurer correctement votre service pour SSL.

Les certificats de gestion que vous associez à votre service ne s'appliquent à votre service que lorsqu'il s'exécute dans le cloud. Lorsque votre service s'exécute dans l'environnement de développement local, il utilise un certificat standard géré par l'émulateur de calcul.
