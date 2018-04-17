---
title: 'Comment : gérer une galerie privée à l’aide de paramètres de Registre | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSIX private galleries, managing
- managing VSIX private galleries
ms.assetid: 86b86442-4293-4cad-9fe2-876eef65f426
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c9631ffa4bce25752b838a78f306ddd3c2313a20
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-manage-a-private-gallery-by-using-registry-settings"></a>Comment : gérer une galerie privée à l’aide des paramètres du Registre
Si vous êtes un administrateur ou le développeur d’une extension de Shell isolé, vous pouvez contrôler l’accès à des contrôles, des modèles et des outils de la galerie Visual Studio, la galerie d’exemples ou des galeries privées. Pour rendre une galerie disponibles ou non disponible, créez un fichier .pkgdef qui décrit les clés de Registre modifiés et leurs valeurs.  
  
## <a name="managing-private-galleries"></a>La gestion des galeries privées  
 Vous pouvez créer un fichier .pkgdef pour contrôler l’accès aux galeries sur plusieurs ordinateurs. Ce fichier doit avoir le format suivant.  
  
```  
[$RootKey$\ExtensionManager\Repositories\{UniqueGUID}]  
@={URI}  (REG_SZ)  
Disabled=0 | 1 (DWORD)  
Priority=0 (highest priority) ... MaxInt (lowest priority) (DWORD) (uint)  
Protocol=Atom Feed|Sharepoint (REG_SZ)  
DisplayName={DisplayName} (REG_SZ)  
DisplayNameResourceID={ID} (REG_SZ)  
DisplayNamePackageGuid={GUID} (REG_SZ)  
  
```  
  
 Le `Repositories` clé fait référence à la galerie pour être activé ou désactivé. La galerie Visual Studio et la galerie d’exemples utilisent le GUID du référentiel suivant :  
  
-   La galerie Visual Studio : 0F45E408-7995-4375-9485-86B8DB553DC9  
  
-   Galerie d’exemples : AEB9CB40-D8E6-4615-B52C-27E307F8506C  
  
 Le `Disabled` valeur est facultative. Par défaut, une galerie est activée.  
  
 Le `Priority` valeur détermine l’ordre dans lequel les galeries sont répertoriés dans la boîte de dialogue Options. La galerie Visual Studio a priorité 10 et la galerie d’exemples a priorité 20. Galeries privées démarrent avec une priorité de 100. Si plusieurs galeries ont la même valeur de priorité, l’ordre dans lequel ils apparaissent est déterminée par les valeurs de leur version localisée `DisplayName` attributs.  
  
 Le `Protocol` valeur est requise pour les galeries basée sur SharePoint ou Atom.  
  
 Soit `DisplayName`, ou les deux `DisplayNameResourceID` et `DisplayNamePackageGuid`, doit être spécifié. Si all est spécifié, le `DisplayNameResourceID` et `DisplayNamePackageGuid` paire est utilisée.  
  
## <a name="disabling-the-visual-studio-gallery-using-a-pkgdef-file"></a>La désactivation de la galerie Visual Studio à l’aide d’un fichier .pkgdef  
 Vous pouvez désactiver une bibliothèque dans un fichier .pkgdef. L’entrée suivante désactive la galerie Visual Studio :  
  
```  
[$RootKey$\ExtensionManager\Repositories\{0F45E408-7995-4375-9485-86B8DB553DC9}]  
"Disabled"=dword:00000001  
  
```  
  
 L’entrée suivante désactive la galerie d’exemples :  
  
```  
[$RootKey$\ExtensionManager\Repositories\{AEB9CB40-D8E6-4615-B52C-27E307F8506C}]  
"Disabled"=dword:00000001  
  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Galeries privées](../extensibility/private-galleries.md)