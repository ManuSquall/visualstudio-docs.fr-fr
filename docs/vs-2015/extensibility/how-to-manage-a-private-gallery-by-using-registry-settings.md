---
title: 'Procédure : gérer une galerie privée à l’aide des paramètres du Registre | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204157"
---
# <a name="how-to-manage-a-private-gallery-by-using-registry-settings"></a>Guide pratique pour gérer une galerie privée à l’aide des paramètres du registre
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Si vous êtes administrateur ou développeur d’une extension de Shell isolé, vous pouvez contrôler l’accès aux contrôles, aux modèles et aux outils de la Galerie Visual Studio, de la Galerie d’exemples ou de galeries privées. Pour rendre une galerie disponible ou non, créez un fichier. pkgdef qui décrit les clés de Registre modifiées et leurs valeurs.  
  
## <a name="managing-private-galleries"></a>Gestion des galeries privées  
 Vous pouvez créer un fichier. pkgdef pour contrôler l’accès aux galeries sur plusieurs ordinateurs. Ce fichier doit avoir le format suivant.  
  
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
  
 La `Repositories` clé fait référence à la galerie à activer ou à désactiver. La Galerie Visual Studio et la Galerie d’exemples utilisent les GUID de référentiel suivants :  
  
- Galerie Visual Studio : 0F45E408-7995-4375-9485-86B8DB553DC9  
  
- Galerie d’exemples : AEB9CB40-D8E6-4615-B52C-27E307F8506C  
  
  La `Disabled` valeur est facultative. Par défaut, une galerie est activée.  
  
  La `Priority` valeur détermine l’ordre dans lequel les galeries sont répertoriées dans la boîte de dialogue Options. La Galerie Visual Studio a la priorité 10 et la Galerie d’exemples a la priorité 20. Les galeries privées commencent à la priorité 100. Si plusieurs galeries ont la même valeur de priorité, l’ordre dans lequel elles apparaissent est déterminé par les valeurs de leurs attributs localisés `DisplayName` .  
  
  La `Protocol` valeur est requise pour les galeries basées sur Atom ou sur SharePoint.  
  
  `DisplayName`Ou bien, `DisplayNameResourceID` et `DisplayNamePackageGuid` doivent être spécifiés. Si tous les sont spécifiés, `DisplayNameResourceID` la `DisplayNamePackageGuid` paire et est utilisée.  
  
## <a name="disabling-the-visual-studio-gallery-using-a-pkgdef-file"></a>Désactivation de la Galerie Visual Studio à l’aide d’un fichier. pkgdef  
 Vous pouvez désactiver une galerie dans un fichier. pkgdef. L’entrée suivante désactive la Galerie Visual Studio :  
  
```  
[$RootPath$\ExtensionManager\Repositories\{0F45E408-7995-4375-9485-86B8DB553DC9}]  
"Disabled"=dword:00000001  
  
```  
  
 L’entrée suivante désactive la Galerie d’exemples :  
  
```  
[$RootPath$\ExtensionManager\Repositories\{AEB9CB40-D8E6-4615-B52C-27E307F8506C}]  
"Disabled"=dword:00000001  
  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Galeries privées](../extensibility/private-galleries.md)
