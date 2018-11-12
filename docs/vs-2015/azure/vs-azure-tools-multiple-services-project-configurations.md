---
title: Configuration de votre projet Azure à l’aide de plusieurs configurations de service | Microsoft Docs
description: Découvrez comment configurer un projet de service cloud Azure en modifiant les fichiers ServiceDefinition.csdef, ServiceConfiguration.Local.cscfg et ServiceConfiguration.Cloud.cscfg.
author: ghogen
manager: douge
assetId: a4fb79ed-384f-4183-9f74-5cac257206b9
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/11/2017
ms.author: ghogen
ms.openlocfilehash: f309c2a960d011601a9fdd41e29d767c667de838
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2018
ms.locfileid: "51002001"
---
# <a name="configuring-your-azure-project-in-visual-studio-to-use-multiple-service-configurations"></a>Configuration de votre projet Azure dans Visual Studio pour utiliser plusieurs configurations de service

Un projet de service cloud Azure dans Visual Studio comprend trois fichiers de configuration : `ServiceDefinition.csdef`, `ServiceConfiguration.Local.cscfg`, et `ServiceConfiguration.Cloud.cscfg`:

- `ServiceDefinition.csdef` est déployé sur Azure pour décrire la configuration requise du service cloud et ses rôles et pour fournir des paramètres qui s’appliquent à toutes les instances. Paramètres peuvent être lus lors de l’exécution à l’aide de l’API Azure Service Hosting Runtime. Ce fichier peut être mis à jour sur Azure uniquement lorsque le service cloud est arrêté.
- `ServiceConfiguration.Local.cscfg` et `ServiceConfiguration.Cloud.cscfg` fournissent les valeurs des paramètres dans la définition de fichier et spécifient le nombre d’instances à exécuter pour chaque rôle. Le fichier « Local » contient des valeurs utilisées dans le débogage local ; le fichier « Cloud » est déployé dans Azure en tant que `ServiceConfiguration.cscfg` et fournit des paramètres pour l’environnement de serveur. Ce fichier peut être mis à jour pendant l’exécution de votre service cloud dans Azure.

Paramètres de configuration sont gérés et modifiés dans Visual Studio à l’aide des pages de propriétés pour le rôle applicable (cliquez sur le rôle et sélectionnez **propriétés**, ou double-cliquez sur le rôle). Modifications peuvent être limitées à la configuration choisie dans la **Configuration du Service** liste déroulante. Les propriétés des rôles web et worker sont similaires, sauf si décrites dans les sections suivantes.

![VS_Solution_Explorer_Roles_Properties](./media/vs-azure-tools-multiple-services-project-configurations/IC784076.png)

Pour plus d’informations sur les schémas sous-jacents de la définition de service et les fichiers de configuration de service, consultez le [schéma XML .csdef](/azure/cloud-services/schema-csdef-file.md) et [schéma XML .cscfg](/azure/cloud-services/schema-cscfg-file.md) articles. Pour plus d’informations sur la configuration du service, consultez [comment configurer les Services de Cloud](/azure/cloud-services/cloud-services-how-to-configure-portal).


## <a name="configuration-page"></a>Page de configuration

### <a name="service-configuration"></a>Configuration du service

Sélectionne le `ServiceConfiguration.*.cscfg` fichier est affecté par les modifications. Par défaut, il existe des variantes Local et Cloud, et vous pouvez utiliser le **gérer...**  commande pour copier, renommer et supprimer des fichiers de configuration. Ces fichiers sont ajoutés à votre projet de service cloud et s’affichent dans **l’Explorateur de solutions**. Cependant, les renommer ou supprimer des configurations peut être effectuée uniquement à partir de ce contrôle.

### <a name="instances"></a>Instances

Définir le **Instance** count propriété pour le nombre d’instances du service doit s’exécuter pour ce rôle.

Définir le **taille de machine virtuelle** propriété **très petite**, **petit**, **support**, **Large**, ou **Extra-large**.  Pour plus d’informations, consultez [tailles de Services Cloud](/azure/cloud-services/cloud-services-sizes-specs).

### <a name="startup-action-web-role-only"></a>Action de démarrage (rôle Web uniquement)

Définissez cette propriété pour spécifier que Visual Studio doit lancer un navigateur web pour les points de terminaison HTTP ou les points de terminaison HTTPS lorsque vous démarrez le débogage.

Le **point de terminaison HTTPS** option est disponible uniquement si vous avez déjà défini un point de terminaison HTTPS pour votre rôle. Vous pouvez définir un point de terminaison HTTPS sur le **points de terminaison** page de propriétés.

Si vous avez déjà ajouté un point de terminaison HTTPS, l’option de point de terminaison HTTPS est activée par défaut, et Visual Studio lance un navigateur pour ce point de terminaison lorsque vous démarrez le débogage, ainsi qu’un navigateur pour votre point de terminaison HTTP, en supposant que les deux options de démarrage sont activées.

### <a name="diagnostics"></a>Diagnostics

Par défaut, les diagnostics sont activés pour le rôle Web. Le compte de stockage et de projet de service cloud Azure sont définies pour utiliser l’émulateur de stockage local. Lorsque vous êtes prêt à déployer sur Azure, vous pouvez sélectionner le bouton Générateur (**...** ) à utiliser le stockage Azure à la place. Vous pouvez transférer les données de diagnostic pour le compte de stockage à la demande ou à intervalles planifiés automatiquement. Pour plus d’informations sur les diagnostics Azure, consultez [activation des Diagnostics dans Azure Cloud Services et Machines virtuelles](/azure/cloud-services/cloud-services-dotnet-diagnostics).

## <a name="settings-page"></a>Page Paramètres

Sur le **paramètres** page, vous pouvez ajouter des paramètres à une configuration en tant que paires nom-valeur. Code exécuté dans le rôle peut lire les valeurs des paramètres de configuration lors de l’exécution à l’aide des classes fournies par le [bibliothèque managée Azure](http://go.microsoft.com/fwlink?LinkID=171026), plus précisément, le [GetConfigurationSettingValue](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleenvironment.getconfigurationsettingvalue.aspx) (méthode).

### <a name="configuring-a-connection-string-for-a-storage-account"></a>Configuration d’une chaîne de connexion pour un compte de stockage

Une chaîne de connexion est un paramètre qui fournit des informations de connexion et d’authentification pour l’émulateur de stockage ou un compte de stockage Azure. Chaque fois que le code dans un rôle accède au stockage Azure (objets BLOB, files d’attente ou tables), il a besoin d’une chaîne de connexion.

> [!Note]
> Une chaîne de connexion pour le compte de stockage Azure doit utiliser un format défini (consultez [configuration des chaînes de connexion stockage Azure](/azure/storage/common/storage-configure-connection-string)).

Le service cloud, vous pouvez définir la chaîne de connexion pour utiliser le stockage local en fonction des besoins, puis définissez sur un compte de stockage Azure lorsque vous déployez l’application. Échec de définition de la chaîne de connexion correctement risque de votre rôle ne pas démarrer, ou alterner entre les États initialisation, occupés et arrêt.

Pour créer une chaîne de connexion, sélectionnez **ajouter un paramètre** et définissez **Type** à « Connection String ».

Pour les chaînes de connexion nouvelle ou existante, sélectionnez **...** * à droite de la **valeur** champ pour ouvrir la **créer une chaîne de connexion stockage** boîte de dialogue :

1. Sous **se connecter à l’aide de**, choisissez le **votre abonnement** possibilité de sélectionner un compte de stockage à partir d’un abonnement. Visual Studio obtient ensuite les informations d’identification du compte de stockage automatiquement à partir de la `.publishsettings` fichier.
1. En sélectionnant **manuellement les informations d’identification entrées** vous permet de spécifiez le nom du compte et clé directement à l’aide des informations à partir du portail Azure. Pour copier la clé de compte :
    1. Accédez au compte de stockage sur le portail Azure et sélectionnez **gérer les clés**.
    1. Pour copier la clé de compte, accédez au compte de stockage sur le portail Azure, sélectionnez **Paramètres > clés d’accès**, puis utilisez le bouton Copier pour copier la clé primaire dans le Presse-papiers.
1. Sélectionnez une des options de connexion. **Spécifiez les points de terminaison personnalisés** vous invite à spécifier des URL spécifiques pour les objets BLOB, tables et les files d’attente. Points de terminaison personnalisés permettent d’utiliser [domaines personnalisés](/azure/storage/blobs/storage-custom-domain-name.md) et pour contrôler plus précisément l’accès. Consultez [configuration des chaînes de connexion de stockage Azure](/azure/storage/common/storage-configure-connection-string).
1. Sélectionnez **OK**, puis **fichier > Enregistrer** pour mettre à jour la configuration avec la nouvelle chaîne de connexion.

Là encore, lorsque vous publiez votre application dans Azure, choisissez la configuration du service qui contient le compte de stockage Azure pour la chaîne de connexion. Une fois que votre application est publiée, vérifiez que l’application fonctionne comme prévu en fonction des services de stockage Azure.

Pour plus d’informations sur comment mettre à jour les configurations de service, consultez la section [gérer les chaînes de connexion pour les comptes de stockage](vs-azure-tools-configure-roles-for-cloud-service.md#manage-connection-strings-for-storage-accounts).

## <a name="endpoints-page"></a>Page points de terminaison

En règle générale, un rôle web a un seul point de terminaison HTTP sur le port 80. Un rôle de travail, en revanche, peut avoir autant de points de terminaison HTTP, HTTPS ou TCP. Points de terminaison peuvent être des points de terminaison d’entrée qui sont disponibles pour les clients externes, ou des points de terminaison internes, qui sont disponibles à d’autres rôles qui sont exécutent dans le service.

- Pour rendre un point de terminaison HTTP accessible aux clients externes et les navigateurs Web, modifiez le type de point de terminaison d’entrée et spécifiez un nom et un numéro de port public.
- Pour rendre un point de terminaison HTTPS disponible aux clients externes et les navigateurs Web, modifiez le type de point de terminaison **d’entrée**et spécifiez un nom, un numéro de port public et un nom de certificat de gestion. Vous devez également définir le certificat sur le **certificats** page de propriétés avant de pouvoir spécifier un certificat de gestion. 
- Pour rendre un point de terminaison disponible pour un accès interne par les autres rôles dans le service cloud, changez le type de point de terminaison interne et spécifiez un nom et des ports privés potentiels pour ce point de terminaison.

## <a name="local-storage-page"></a>Page de stockage local

Vous pouvez utiliser la **stockage Local** réserver une ou plusieurs ressources de stockage local pour un rôle de la page de propriétés. Une ressource de stockage local est un répertoire réservé dans le système de fichiers de la machine virtuelle Azure dans lequel une instance d’un rôle est en cours d’exécution.

## <a name="certificates-page"></a>Page certificats

Le **certificats** page de propriétés ajoute des informations sur vos certificats à votre configuration de service. Notez que vos certificats ne sont pas empaquetés avec votre service ; Vous devez télécharger séparément vos certificats à Azure via le [Azure portal](http://portal.azure.com).

Ajout d’un certificat ici ajoute des informations sur vos certificats à votre configuration de service. Les certificats ne sont pas empaquetés avec le service ; Vous devez télécharger vos certificats séparément par le biais du portail Azure.

Pour associer un certificat à votre rôle, fournissez un nom pour le certificat. Vous utilisez ce nom pour faire référence au certificat lorsque vous configurez un point de terminaison HTTPS sur le **points de terminaison** page. Ensuite, spécifiez si le magasin de certificats est **ordinateur Local** ou **utilisateur actuel** et le nom du magasin. Enfin, entrez l’empreinte du certificat. Si le certificat est dans utilisateur actuel\mon magasin (My), vous pouvez entrer l’empreinte du certificat en sélectionnant le certificat à partir d’une liste. Si elle se trouve dans un autre emplacement, entrez la valeur d’empreinte numérique à la main.

Lorsque vous ajoutez un certificat du magasin de certificats, tous les certificats intermédiaires sont automatiquement ajoutés aux paramètres de configuration pour vous. En outre, ces certificats intermédiaires doivent être téléchargés vers Azure pour configurer correctement votre service pour SSL.

Les certificats de gestion que vous associez à votre service s’appliquent à votre service uniquement lorsqu’il s’exécute dans le cloud. Lorsque votre service s’exécute dans l’environnement de développement local, il utilise un certificat standard géré par l’émulateur de calcul.
