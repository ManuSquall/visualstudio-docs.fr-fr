---
title: Ressources dans les VSPackages | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managed VSPackages, resources in
- resources, managed VSPackages
- VSPackages, managed resources
ms.assetid: cc8c17a6-b190-4856-b001-0c1104f104b2
caps.latest.revision: 23
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: eb5c9550fd29b0e98bf63a7240737da4f13f3249
ms.openlocfilehash: 8a49aa40daaa1bd0fc0543d2f6198212185c8490
ms.contentlocale: fr-fr
ms.lasthandoff: 09/06/2017

---
# <a name="resources-in-vspackages"></a>Ressources dans les VSPackages
Vous pouvez incorporer des ressources localisées dans native UI les DLL satellites, les DLL satellites managées, ou dans un VSPackage managé lui-même.  
  
 Certaines ressources ne peut pas être incorporés dans des VSPackages. Les types managés suivantes peuvent être intégrés :  
  
-   Chaînes  
  
-   Clés de chargement de package (qui sont également des chaînes)  
  
-   Icônes de fenêtre outil  
  
-   Fichiers de sortie de Table de commande (CTO) compilés  
  
-   CTO bitmaps  
  
-   Aide en ligne de commande  
  
-   À propos des données de boîte de dialogue  
  
 Les ressources dans un package managé sont sélectionnées par l’ID de ressource. Une exception est le fichier CTO, qui doit être nommé CTMENU. Le fichier CTO doit apparaître dans la table de ressources comme un `byte[]`. Tous les autres éléments de ressource sont identifiés par type.  
  
 Vous pouvez utiliser la <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> attribut pour indiquer à [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] que les ressources managées sont disponibles.  
  
 [!code-csharp[VSSDKResources #1](../../extensibility/internals/codesnippet/CSharp/resources-in-vspackages_1.cs) ] [!code-vb [VSSDKResources n° 1](../../extensibility/internals/codesnippet/VisualBasic/resources-in-vspackages_1.vb)]  
  
 Paramètre <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> de cette manière indique que [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] doit ignorer les DLL satellites non managée lors de la recherche pour les ressources, par exemple, à l’aide de <xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackageString%2A>. Si [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] rencontre deux ou plusieurs ressources qui ont le même ID de ressource, il utilise la première ressource qu’il trouve.  
  
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
  
 L’exemple suivant montre comment incorporer le tableau d’octets CTO, qui doit être nommé CTMENU.  
  
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
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]chargement des retards de VSPackages autant que possible. Une conséquence de l’incorporation d’un fichier CTO dans un VSPackage est que [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] doit charger tous les VSPackages telle dans la mémoire pendant l’installation, c'est-à-dire lorsqu’il génère une table de commandes fusionnée. Ressources peuvent être extraites d’un VSPackage en examinant les métadonnées sans exécuter du code dans le VSPackage. Le package Visual Studio n’est pas initialisé à ce stade, par conséquent, la perte de performances est minime.  
  
 Lorsque [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] demande une ressource à partir d’un VSPackage après l’installation, ce package étant susceptible d’être déjà chargé et initialisé, la perte de performances est minime.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des VSPackages](../../extensibility/managing-vspackages.md)   
 [Ressources localisées dans les applications MFC : DLL satellites](/cpp/build/localized-resources-in-mfc-applications-satellite-dlls)   

