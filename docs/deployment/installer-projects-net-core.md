---
title: Projets Visual Studio Installer et .NET Core 3,1
titleSuffix: ''
ms.date: 08/18/2020
ms.topic: conceptual
helpviewer_keywords:
- installer projects
- installer projects, .NETCore
author: MSLukeWest
ms.author: lukewest
manager: MSLukeWest
monikerRange: '>= vs-2019'
ms.workload:
- multiple
ms.openlocfilehash: 86680a2b961af9182691422e02b42c6529f45639
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90852652"
---
# <a name="visual-studio-installer-projects-extension-and-net-core-31"></a>Extension des projets Visual Studio Installer et NET.Core 3.1

L’empaquetage d’applications en tant que MSI est souvent effectué à l’aide de l’extension de projets Visual Studio Installer.

Vous pouvez télécharger l’extension ici : [Visual Studio installer projets](https://marketplace.visualstudio.com/items?itemName=VisualStudioClient.MicrosoftVisualStudio2017InstallerProjects)

## <a name="update-for-net-core"></a>Mise à jour pour .NET Core
.NET Core a deux modèles différents pour la publication.

- Déploiements dépendants du Framework

- Les applications autonomes incluent le Runtime.

Pour en savoir plus sur ces stratégies de déploiement, consultez [vue d’ensemble de la publication d’applications .net Core](/dotnet/core/deploying/).

### <a name="workflow-changes-for-net-core-31"></a>Modifications du flux de travail pour .NET Core 3,1

1. Sélectionnez **publier les éléments** au lieu de la **sortie principale** pour obtenir la sortie correcte pour les projets .net Core 3,1.  Pour afficher cette boîte de dialogue, sélectionnez **Ajouter**  >  la**sortie du projet...** dans le menu contextuel du projet.

    ![Le groupe publier les éléments de sortie dans la boîte de dialogue Ajouter un groupe de sortie de projet](../deployment/media/installer-projects-net-core-publish-items-output.png "Choisir les éléments à publier")

2. Pour créer un programme d’installation autonome, définissez la propriété **PublishProfilePath** sur le nœud **publier les éléments** du projet d’installation, à l’aide du chemin d’accès relatif d’un profil de publication avec les propriétés appropriées définies.

    ![Définition du profil de publication sur l’élément de sortie de projet publier des éléments](../deployment/media/installer-projects-net-core-publish-profile.png "Définir le profil de publication")

### <a name="prerequisites-for-net-core-31"></a>Conditions préalables pour .NET Core 3,1

Si vous souhaitez que votre programme d’installation puisse installer le runtime nécessaire pour une application .NET Core 3,1 dépendante du Framework, vous pouvez effectuer cette opération à l’aide des [composants requis](../deployment/application-deployment-prerequisites.md).  Dans la boîte de dialogue Propriétés de votre projet d’installation, ouvrez la boîte de dialogue **composants requis...** pour afficher les entrées suivantes :

![Éléments .NET Core dans la boîte de dialogue composants requis](../deployment/media/installer-projects-net-core-prerequisites.png "Prérequis pour .NET Core")

L’option **Runtime .net core...** doit être sélectionnée pour les applications console, **.net Desktop Runtime...** doit être sélectionné pour les applications WPF/WinForms.

>[!NOTE]
>Ces éléments sont présents à partir de la version Visual Studio 2019 Update 7.

## <a name="see-also"></a>Voir aussi

- [Composants requis, boîte de dialogue](../ide/reference/prerequisites-dialog-box.md)
- [Conditions préalables pour le déploiement d’applications](../deployment/application-deployment-prerequisites.md)