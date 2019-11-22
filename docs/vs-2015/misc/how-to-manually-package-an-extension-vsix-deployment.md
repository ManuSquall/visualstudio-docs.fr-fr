---
title: 'Comment : empaqueter manuellement une extension (déploiement VSIX) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
ms.assetid: d25990e0-e782-4a79-9d9a-1caf3c56c6a2
caps.latest.revision: 10
manager: jillfra
ms.openlocfilehash: a615aea75ec00e49ee4d2837b8b4e2b1d20d3306
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74293623"
---
# <a name="how-to-manually-package-an-extension-vsix-deployment"></a>Procédure : création manuelle d’un package d’extension (déploiement VSIX)
Vous pouvez créer un package VSIX pour encapsuler une extension [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] pour le déploiement. Il existe trois façons de créer un package :  
  
- Créez un projet de package VSIX avec l’un des modèles d’extensibilité inclus dans le Kit de développement logiciel [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] (SDK). Pour la plupart des scénarios, il s’agit de l’option la plus simple.  
  
- Encapsulez la sortie de votre projet d’extension dans un [projet VSIX](../extensibility/vsix-project-template.md) vide. Cette option est recommandée pour les modèles, les assemblys non pris en charge et les types personnalisés.  
  
- Créez manuellement un package VSIX. Cette option est recommandée uniquement quand les deux autres options ne sont pas disponibles.  
  
  Ce document aborde la troisième option.  
  
## <a name="creating-a-vsix-package"></a>Création d’un package VSIX  
 Pour créer manuellement un package d’extension, ajoutez un fichier extension.manifest et un fichier [Content_Types].xml au projet d’extension. Placez-les dans un fichier compressé avec votre sortie de génération, puis renommez le fichier compressé pour que son extension de nom de fichier soit .vsix. Le type de l’extension doit être pris en charge par le [schéma VSIX](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).  
  
> [!NOTE]
> Les noms de fichiers dans les packages VSIX ne doivent pas inclure d’espaces, ni de caractères réservés dans les URI (Uniform Resource Identifier), comme défini sous [\[\]rfc2396 ](https://go.microsoft.com/fwlink/?LinkId=90339).  
  
#### <a name="to-manually-create-a-vsix-package"></a>Pour créer manuellement un package VSIX  
  
1. Créez une extension Visual Studio d’un type pris en charge par le schéma VSIX.  
  
2. Créez un fichier XML, puis nommez-le `extension.vsixmanifest`.  
  
3. Remplissez le fichier extension.vsixmanifest selon le schéma VSIX. Pour obtenir un exemple de manifeste, consultez [PackageManifest Element (Root Element, VSX Schema)](https://msdn.microsoft.com/f8ae42ba-775a-4d2b-976a-f556e147f187).  
  
4. Créez un deuxième fichier XML, puis nommez-le `[Content_Types].xml`.  
  
5. Renseignez le fichier [Content_Types]. XML comme indiqué dans [la structure du fichier Content_types\]. xml](../extensibility/the-structure-of-the-content-types-dot-xml-file.md).  
  
6. Placez les deux fichiers XML dans un répertoire avec l’extension à déployer.  
  
     Dans le cas d’un modèle de projet ou d’un modèle d’élément, placez le fichier .zip qui contient le modèle dans le même dossier que les fichiers XML. Ne placez pas les fichiers XML dans le fichier .zip.  
  
     Dans tous les autres cas, placez les fichiers XML dans le même répertoire que la sortie de génération.  
  
7. Dans l’Explorateur Windows, cliquez avec le bouton droit sur le dossier qui contient le contenu de l’extension et les deux fichiers XML, cliquez sur **Envoyer vers**, puis cliquez sur **Dossier compressé**.  
  
8. Renommez le fichier .zip que vous venez de créer *nom_fichier*.vsix, où *nom_fichier* correspond au nom du fichier redistribuable qui installe votre package.  
  
## <a name="see-also"></a>Voir aussi  
 [Expédition des extensions Visual Studio](../extensibility/shipping-visual-studio-extensions.md)   
 [Anatomie d’un package VSIX](../extensibility/anatomy-of-a-vsix-package.md)   
 [Élément PackageManifest (élément racine, schéma VSX)](https://msdn.microsoft.com/f8ae42ba-775a-4d2b-976a-f556e147f187)