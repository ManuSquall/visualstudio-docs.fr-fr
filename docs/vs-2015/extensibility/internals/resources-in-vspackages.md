---
title: Ressources dans VSPackages | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- managed VSPackages, resources in
- resources, managed VSPackages
- VSPackages, managed resources
ms.assetid: cc8c17a6-b190-4856-b001-0c1104f104b2
caps.latest.revision: 24
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 073245be91c1689d0dd70d30207dc4dd809c578e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49188569"
---
# <a name="resources-in-vspackages"></a>Ressources dans VSPackages
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Vous pouvez incorporer des ressources localisées dans native interface utilisateur les DLL satellites, les DLL satellites managées, ou dans un VSPackage managé lui-même.  
  
 Certaines ressources ne peut pas être incorporés dans les VSPackages. Les types managés suivants peuvent être incorporés :  
  
-   Chaînes  
  
-   Clés de chargement de package (qui sont également des chaînes)  
  
-   Icônes de fenêtre outil  
  
-   Fichiers de sortie de Table de commande (directeur) compilés  
  
-   Bitmaps de directeur technique  
  
-   Aide en ligne de commande  
  
-   À propos des données de boîte de dialogue  
  
 Ressources dans un package managé sont sélectionnées par l’ID de ressource. Une exception est le fichier de directeur technique, qui doit être nommé CTMENU. Le fichier de directeur technique doit apparaître dans la table de ressources comme un `byte[]`. Tous les autres éléments de ressource sont identifiés par type.  
  
 Vous pouvez utiliser la <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> attribut pour indiquer au [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] que les ressources managées sont disponibles.  
  
 [!code-csharp[VSSDKResources#1](../../snippets/csharp/VS_Snippets_VSSDK/vssdkresources/cs/vssdkresourcespackage.cs#1)]
 [!code-vb[VSSDKResources#1](../../snippets/visualbasic/VS_Snippets_VSSDK/vssdkresources/vb/vssdkresourcespackage.vb#1)]  
  
 Paramètre <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> de cette manière indique que [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] doit ignorer la DLL satellites non géré lorsqu’il recherche des ressources, par exemple, à l’aide de <xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackageString%2A>. Si [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] rencontre deux ou plusieurs ressources qui ont le même ID de ressource, il utilise la première ressource qu’il trouve.  
  
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
  
 L’exemple suivant montre comment incorporer le tableau d’octets de directeur technique, qui doit être nommé CTMENU.  
  
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
  
## <a name="implementation-notes"></a>Remarques d’implémentation  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] chargement des retards de VSPackages autant que possible. Des conséquences de l’incorporation d’un fichier de directeur technique dans un VSPackage est que [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] doit charger tous les packages de ce type dans la mémoire pendant l’installation, c'est-à-dire lorsqu’il génère une table de commandes fusionnée. Ressources peuvent être extraites d’un VSPackage en examinant les métadonnées sans exécuter le code dans le VSPackage. Le VSPackage n’est pas initialisé à ce stade, la perte de performances est minime.  
  
 Lorsque [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] demandes une ressource à partir d’un VSPackage après l’installation, ce package étant susceptible d’être déjà chargé et initialisé, la perte de performances est minime.  
  
## <a name="see-also"></a>Voir aussi  
 [VSPackages gérés](../../misc/managed-vspackages.md)   
 [Gestion de VSPackages](../../extensibility/managing-vspackages.md)   
 [Ressources localisées dans des Applications MFC : DLL satellites](http://msdn.microsoft.com/library/3a1100ae-a9c8-47b5-adbd-cbedef5992ef)   
 [VSPackages gérés](../../misc/managed-vspackages.md)

