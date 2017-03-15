---
title: Ressources dans les packages VS | Documents Microsoft
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
translationtype: Machine Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 184642501b9452566a15e1aba30312e17500f7bb
ms.lasthandoff: 02/22/2017

---
# <a name="resources-in-vspackages"></a>Ressources dans les packages VS
Vous pouvez incorporer des ressources localisées dans native interface DLL satellites, DLL satellites managées, ou dans un VSPackage managé lui-même.  
  
 Certaines ressources ne peut pas être incorporés dans les VSPackages. Les types managés suivants peuvent être intégrés :  
  
-   Chaînes  
  
-   Clés de chargement de package (qui sont également des chaînes)  
  
-   Icônes de fenêtre outil  
  
-   Fichiers de sortie de Table de commande (CTO) compilés  
  
-   Bitmaps de directeur technique  
  
-   Aide en ligne de commande  
  
-   À propos des données de boîte de dialogue  
  
 Ressources dans un package managé sont sélectionnées par l’ID de ressource. Une exception est le fichier directeur technique, qui doit être nommé CTMENU. Le fichier CTO doit apparaître dans la table de ressources comme un `byte[]`. Tous les autres éléments de ressource sont identifiés par type.  
  
 Vous pouvez utiliser la <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>attribut pour indiquer au [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] que les ressources managées sont disponibles.</xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>  
  
 [!code-cs[N °&1; de VSSDKResources](../../extensibility/internals/codesnippet/CSharp/resources-in-vspackages_1.cs)]
 [!code-vb[VSSDKResources n °&1;](../../extensibility/internals/codesnippet/VisualBasic/resources-in-vspackages_1.vb)]  
  
 Paramètre <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>de cette manière indique que [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] doit ignorer la DLL satellites non managée lors de la recherche de ressources, par exemple, à l’aide <xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackageString%2A>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackageString%2A> </xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> Si [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] rencontre deux ou plusieurs ressources qui ont le même ID de ressource, il utilise la première ressource qu’il trouve.  
  
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
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]chargement des retards de packages VS autant que possible. Une conséquence de l’incorporation d’un fichier de directeur technique dans un VSPackage est que [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] doit charger tous ces packages VS en mémoire pendant l’installation, c'est-à-dire lorsqu’il génère une table de commandes fusionnée. Ressources peuvent être extraites d’un VSPackage en examinant les métadonnées sans exécuter le code dans le VSPackage. Le VSPackage n’est pas initialisé à ce stade, la perte de performances est minime.  
  
 Lorsque [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] demande une ressource à partir d’un VSPackage après l’installation, ce package est probablement déjà chargé et initialisé, la perte de performances est minime.  
  
## <a name="see-also"></a>Voir aussi  
 [VSPackages gérés](../../misc/managed-vspackages.md)   
 [La gestion de packages VS](../../extensibility/managing-vspackages.md)   
 [Ressources localisées dans des Applications MFC : DLL satellites](http://msdn.microsoft.com/Library/3a1100ae-a9c8-47b5-adbd-cbedef5992ef)   
 [VSPackages gérés](../../misc/managed-vspackages.md)
