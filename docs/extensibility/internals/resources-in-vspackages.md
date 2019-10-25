---
title: Ressources dans les VSPackages | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- managed VSPackages, resources in
- resources, managed VSPackages
- VSPackages, managed resources
ms.assetid: cc8c17a6-b190-4856-b001-0c1104f104b2
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 07e1e19f802203b9770764330ea894b7d0eb98b8
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72724157"
---
# <a name="resources-in-vspackages"></a>Ressources dans VSPackages
Vous pouvez incorporer des ressources localisées dans des dll d’interface utilisateur satellite natives, des dll satellites managées ou dans un VSPackage géré lui-même.

 Certaines ressources ne peuvent pas être incorporées dans les VSPackages. Les types managés suivants peuvent être incorporés :

- Chaînes

- Clés de chargement de package (qui sont également des chaînes)

- Icônes de la fenêtre outil

- Fichiers de sortie de la table de commandes compilés (directeur technique)

- Bitmaps de directeur technique

- Aide sur la ligne de commande

- À propos des données de boîte de dialogue

  Les ressources d’un package géré sont sélectionnées par l’ID de ressource. Le fichier de directeur technique, qui doit être nommé CTMENU, est une exception. Le fichier de directeur technique doit apparaître dans la table de ressources en tant que `byte[]`. Tous les autres éléments de ressource sont identifiés par type.

  Vous pouvez utiliser l’attribut <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> pour indiquer à [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] que les ressources managées sont disponibles.

  [!code-csharp[VSSDKResources#1](../../extensibility/internals/codesnippet/CSharp/resources-in-vspackages_1.cs)]
  [!code-vb[VSSDKResources#1](../../extensibility/internals/codesnippet/VisualBasic/resources-in-vspackages_1.vb)]

  La définition de <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> de cette manière indique que [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] doit ignorer les dll satellites non managées lors de la recherche de ressources, par exemple, à l’aide de <xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackageString%2A>. Si [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] rencontre deux ressources ou plus qui ont le même ID de ressource, elle utilise la première ressource qu’elle trouve.

## <a name="example"></a>Exemple
 L’exemple suivant est une représentation managée d’une icône de fenêtre outil.

```
<data name="1001"
type="System.Resources.ResXFileRef,System.Windows.Forms">
     <value>
     MyToolWinIcon.bmp;
     System.Drawing.Bitmap,
     System.Drawing,
     Version=1.0.0.0,
     Culture=neutral,
     PublicKeyToken=b03f5f7f11d50a3a
     </value>
</data>
```

 L’exemple suivant montre comment incorporer le tableau d’octets de la directeur de la configuration, qui doit être nommé CTMENU.

```
<data name="CTMENU"
type="System.Resources.ResXFileRef,System.Windows.Forms">
     <value>
     MyPackage.cto;
     System.Byte[],
     mscorlib,
     Version=1.0.0.0,
     Culture=neutral,
     PublicKeyToken=b03f5f7f11d50a3a
     </value>
</data>
```

## <a name="implementation-notes"></a>Remarques sur l’implémentation
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] retarde le chargement des VSPackages chaque fois que cela est possible. La conséquence de l’incorporation d’un fichier de directeur technique dans un VSPackage est que [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] devez charger tous ces VSPackages en mémoire lors de l’installation, ce qui correspond à la création d’une table de commandes fusionnée. Les ressources peuvent être extraites d’un VSPackage en examinant les métadonnées sans exécuter de code dans le VSPackage. Le VSPackage n’est pas initialisé pour l’instant, la perte de performances est donc minime.

 Lorsque [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] demande une ressource à partir d’un VSPackage après l’installation, ce package est susceptible d’être déjà chargé et initialisé, de sorte que la perte de performances est minime.

## <a name="see-also"></a>Voir aussi
- [Gestion de VSPackages](../../extensibility/managing-vspackages.md)
- [Ressources localisées dans les applications MFC : DLL satellites](/cpp/build/localized-resources-in-mfc-applications-satellite-dlls)
