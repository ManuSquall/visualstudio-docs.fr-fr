---
title: Gestion des rôles dans Azure cloud services avec Visual Studio | Microsoft Docs
description: Découvrez comment ajouter et supprimer des rôles dans Azure cloud services avec Visual Studio.
author: ghogen
manager: douge
assetId: 5ec9ae2e-8579-4e5d-999e-8ae05b629bd1
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 03/21/2017
ms.author: ghogen
ms.openlocfilehash: 35221cbf98f26a71e2b4adf0a7178342616ff7c0
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2018
ms.locfileid: "51001976"
---
# <a name="managing-roles-in-azure-cloud-services-with-visual-studio"></a>Gestion des rôles dans Azure cloud services avec Visual Studio
Une fois que vous avez créé votre service cloud Azure, vous pouvez ajouter de nouveaux rôles ou supprimer des rôles existants à partir de celui-ci. Vous pouvez également importer un projet existant et la convertir en un rôle. Par exemple, vous pouvez importer une application web ASP.NET et désigner comme un rôle web.

## <a name="adding-a-role-to-an-azure-cloud-service"></a>Ajout d’un rôle à un service cloud Azure
Les étapes suivantes vous guident tout au long de l’ajout d’un rôle web ou de travail à un projet de service cloud Azure dans Visual Studio.

1. Créez ou ouvrez un projet de service cloud Azure dans Visual Studio.

1. Dans **l’Explorateur de solutions**, développez le nœud du projet

1. Cliquez sur le **rôles** nœud pour afficher le menu contextuel. Dans le menu contextuel, sélectionnez **ajouter**, puis sélectionnez un rôle web existant ou un rôle de travail à partir de la solution actuelle ou créez un projet de rôle web ou de travail. Vous pouvez également sélectionner un projet approprié, par exemple un projet d’application web ASP.NET et l’associer à un projet de rôle.

    ![Options de menu pour ajouter un rôle à un projet de service cloud Azure](./media/vs-azure-tools-cloud-service-project-managing-roles/add-role.png)

## <a name="removing-a-role-from-an-azure-cloud-service"></a>Suppression d’un rôle à partir d’un service cloud Azure
Les étapes suivantes vous guident lors de la suppression d’un rôle web ou de travail à partir d’un projet de service cloud Azure dans Visual Studio.

1. Créez ou ouvrez un projet de service cloud Azure dans Visual Studio.

1. Dans **l’Explorateur de solutions**, développez le nœud du projet

1. Développez le **rôles** nœud.

1. Cliquez sur le nœud que vous souhaitez supprimer, puis, dans le menu contextuel, sélectionnez **supprimer**. 

    ![Options de menu pour ajouter un rôle à un service cloud Azure](./media/vs-azure-tools-cloud-service-project-managing-roles/remove-role.png)

## <a name="readding-a-role-to-an-azure-cloud-service-project"></a>Réajout d’un rôle à un projet de service cloud Azure
Si vous supprimez un rôle à partir de votre projet de service cloud mais décidez ensuite d’ajouter le rôle dans le projet, uniquement la déclaration de rôle et les attributs de base, telles que des points de terminaison et informations de diagnostic, sont ajoutés. Aucune ressource ou référence supplémentaire n’est ajoutés à la `ServiceDefinition.csdef` fichier ou à la `ServiceConfiguration.cscfg` fichier. Si vous souhaitez ajouter ces informations, vous devez l’ajouter manuellement à ces fichiers.

Par exemple, vous pouvez supprimer un rôle de service web et que vous décidez ensuite d’ajouter ce rôle dans votre solution. Dans ce cas, une erreur se produit. Pour éviter cette erreur, vous devez ajouter le `<LocalResources>` élément présenté dans le code XML suivant dans le `ServiceDefinition.csdef` fichier. Utilisez le nom du rôle de service web que vous avez réintégré dans le projet dans le cadre de l’attribut de nom pour le **<LocalStorage>** élément. Dans cet exemple, le nom du rôle de service web est **WCFServiceWebRole1**.

    <WebRole name="WCFServiceWebRole1">
        <Sites>
          <Site name="Web">
            <Bindings>
              <Binding name="Endpoint1" endpointName="Endpoint1" />
            </Bindings>
          </Site>
        </Sites>
        <Endpoints>
          <InputEndpoint name="Endpoint1" protocol="http" port="80" />
        </Endpoints>
        <Imports>
          <Import moduleName="Diagnostics" />
        </Imports>
       <LocalResources>
          <LocalStorage name="WCFServiceWebRole1.svclog" sizeInMB="1000" cleanOnRoleRecycle="false" />
       </LocalResources>
    </WebRole>

## <a name="next-steps"></a>Étapes suivantes
- [Configurer les rôles pour un service cloud Azure avec Visual Studio](vs-azure-tools-configure-roles-for-cloud-service.md)
