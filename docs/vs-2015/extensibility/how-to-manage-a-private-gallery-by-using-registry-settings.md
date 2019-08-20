---
title: 'Procédure : Gérer une galerie privée à l’aide des paramètres du Registre | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSIX private galleries, managing
- managing VSIX private galleries
ms.assetid: 86b86442-4293-4cad-9fe2-876eef65f426
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a55b7aa486edfd3775b12dca9d143c2e5f280884
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68204157"
---
# <a name="how-to-manage-a-private-gallery-by-using-registry-settings"></a>Procédure : Gérer une galerie privée à l’aide des paramètres du Registre
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Si vous êtes un administrateur ou le développeur d’une extension de Shell isolé, vous pouvez contrôler l’accès à des contrôles, des modèles et des outils dans la galerie Visual Studio, la galerie d’exemples ou des galeries privées. Pour activer ou désactiver les une galerie, créez un fichier .pkgdef qui décrit les clés de Registre modifiés et leurs valeurs.  
  
## <a name="managing-private-galleries"></a>La gestion des galeries privées  
 Vous pouvez créer un fichier .pkgdef pour contrôler l’accès aux galeries sur plusieurs ordinateurs. Ce fichier doit avoir le format suivant.  
  
```  
[$RootPath$\ExtensionManager\Repositories\{UniqueGUID}]  
@={URI}  (REG_SZ)  
Disabled=0 | 1 (DWORD)  
Priority=0 (highest priority) … MaxInt (lowest priority) (DWORD) (uint)  
Protocol=Atom Feed|Sharepoint (REG_SZ)  
DisplayName={DisplayName} (REG_SZ)  
DisplayNameResourceID={ID} (REG_SZ)  
DisplayNamePackageGuid={GUID} (REG_SZ)  
  
```  
  
 Le `Repositories` clé fait référence à la galerie pour être activé ou désactivé. La galerie Visual Studio et la galerie d’exemples utilisent le GUID du référentiel suivant :  
  
- Galerie Visual Studio : 0F45E408-7995-4375-9485-86B8DB553DC9  
  
- Galerie d’exemples : AEB9CB40-D8E6-4615-B52C-27E307F8506C  
  
  Le `Disabled` valeur est facultative. Par défaut, une galerie est activée.  
  
  Le `Priority` valeur détermine l’ordre dans lequel les galeries sont répertoriés dans la boîte de dialogue Options. Galerie Visual Studio a une priorité 10 et la galerie d’exemples a priorité 20. Galeries privées démarrent à la priorité de 100. Si plusieurs galeries ont la même valeur de priorité, l’ordre dans lequel ils apparaissent est déterminé par les valeurs de leur version localisée `DisplayName` attributs.  
  
  Le `Protocol` valeur est requise pour les galeries basée sur SharePoint ou Atom.  
  
  Soit `DisplayName`, ou les deux `DisplayNameResourceID` et `DisplayNamePackageGuid`, doit être spécifié. Si all est spécifié, puis le `DisplayNameResourceID` et `DisplayNamePackageGuid` paire est utilisée.  
  
## <a name="disabling-the-visual-studio-gallery-using-a-pkgdef-file"></a>La désactivation de la galerie Visual Studio à l’aide d’un fichier .pkgdef  
 Vous pouvez désactiver une galerie dans un fichier .pkgdef. L’entrée suivante désactive la galerie Visual Studio :  
  
```  
[$RootPath$\ExtensionManager\Repositories\{0F45E408-7995-4375-9485-86B8DB553DC9}]  
"Disabled"=dword:00000001  
  
```  
  
 L’entrée suivante désactive la galerie d’exemples :  
  
```  
[$RootPath$\ExtensionManager\Repositories\{AEB9CB40-D8E6-4615-B52C-27E307F8506C}]  
"Disabled"=dword:00000001  
  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Galeries privées](../extensibility/private-galleries.md)
