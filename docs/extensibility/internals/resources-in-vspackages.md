---
title: Ressources dans VSPackages (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- managed VSPackages, resources in
- resources, managed VSPackages
- VSPackages, managed resources
ms.assetid: cc8c17a6-b190-4856-b001-0c1104f104b2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 493e9834e3d7cf6d82cebb8dd93d5369678c7be0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705601"
---
# <a name="resources-in-vspackages"></a>Ressources dans VSPackages
Vous pouvez intégrer des ressources localisées dans les DLL d’interface utilisateur par satellite indigènes, les DLL par satellite gérés ou dans un VSPackage géré lui-même.

 Certaines ressources ne peuvent pas être intégrées dans VSPackages. Les types gérés suivants peuvent être intégrés :

- Chaînes

- Clés de chargement de paquet (qui sont également des cordes)

- Icônes de fenêtre d’outil

- Fichiers de sortie de tableau de commande compileds (CTO)

- Bitmaps CTO

- Aide de commande-ligne

- À propos des données des boîtes de dialogue

  Les ressources d’un ensemble géré sont sélectionnées par pièce d’identité de ressources. Une exception est le fichier CTO, qui doit être nommé CTMENU. Le fichier CTO doit apparaître dans `byte[]`le tableau des ressources comme un . Tous les autres éléments de ressources sont identifiés par type.

  Vous pouvez <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> utiliser l’attribut pour indiquer que des [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ressources gérées sont disponibles.

  [!code-csharp[VSSDKResources#1](../../extensibility/internals/codesnippet/CSharp/resources-in-vspackages_1.cs)]
  [!code-vb[VSSDKResources#1](../../extensibility/internals/codesnippet/VisualBasic/resources-in-vspackages_1.vb)]

  Le <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> réglage de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] cette manière indique que devrait ignorer les DLL satellites non <xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackageString%2A>mentés lorsqu’il recherche des ressources, par exemple, en utilisant . Si [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] elle rencontre deux ressources ou plus qui ont la même pièce d’identité de ressource, elle utilise la première ressource qu’il trouve.

## <a name="example"></a>Exemple
 L’exemple suivant est une représentation gérée d’une icône de fenêtre d’outil.

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

 L’exemple suivant montre comment intégrer le tableau d’ordrices CTO, qui doit être nommé CTMENU.

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

## <a name="implementation-notes"></a>Remarques relatives à l’implémentation
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]retarde le chargement des VSPackages dans la mesure du possible. Une conséquence de l’intégration d’un fichier CTO dans un VSPackage est qui [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] doit charger tous ces VSPackages dans la mémoire pendant la configuration, qui est quand il construit une table de commande fusionnée. Les ressources peuvent être extraites d’un VSPackage en examinant les métadonnées sans avoir de code en cours d’exécution dans le VSPackage. Le VSPackage n’est pas initialisé pour le moment, de sorte que la perte de performance est minime.

 Lorsque [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] demande une ressource d’un VSPackage après la configuration, ce paquet est susceptible d’être déjà chargé et initialisé, de sorte que la perte de performance est minime.

## <a name="see-also"></a>Voir aussi
- [Gestion de VSPackages](../../extensibility/managing-vspackages.md)
- [Ressources localisées dans les applications MFC : DLL satellites](/cpp/build/localized-resources-in-mfc-applications-satellite-dlls)
