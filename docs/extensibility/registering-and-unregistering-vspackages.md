---
title: "Inscription et la désinscription VSPackages | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- registration, VSPackages
- VSPackages, registering
ms.assetid: e25e7a46-6a55-4726-8def-ca316f553d6b
caps.latest.revision: 35
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 73039d6e9bf0db6b3deee00745e21660173f21c0
ms.contentlocale: fr-fr
ms.lasthandoff: 02/22/2017

---
# <a name="registering-and-unregistering-vspackages"></a>Inscription et annulation de l’enregistrement de packages VS
Attributs permet d’enregistrer un VSPackage, mais  
  
## <a name="registering-a-vspackage"></a>L’inscription d’un VSPackage  
 Vous pouvez utiliser des attributs pour contrôler l’enregistrement de packages VS managés. Toutes les informations d’inscription sont contenues dans un fichier .pkgdef. Pour plus d’informations sur l’enregistrement de fichiers, consultez [CreatePkgDef utilitaire](../extensibility/internals/createpkgdef-utility.md).  
  
 Le code suivant montre comment utiliser les attributs d’enregistrement standard pour inscrire votre VSPackage.  
  
```c#  
[PackageRegistration(UseManagedResourcesOnly = true)]  
[Guid("0B81D86C-0A85-4f30-9B26-DD2616447F95")]  
public sealed class BasicPackage : Package  
{. . .}  
```  
  
## <a name="unregistering-an-extension"></a>Annuler l’inscription d’une Extension  
 Si vous réalisé avec un grand nombre de packages VS différents et que vous souhaitez les supprimer de l’instance expérimentale, vous pouvez exécuter la **réinitialiser** commande. Recherchez **réinitialiser l’Instance expérimentale de Visual Studio** sur la page de démarrage de votre ordinateur, ou d’exécuter cette commande à partir de la ligne de commande :  
  
```vb  
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe" /Reset /VSInstance=14.0 /RootSuffix=Exp  
```  
  
 Si vous souhaitez désinstaller une extension que vous avez installés sur votre instance de développement de Visual Studio, accédez à **outils / Extensions et mises à jour**, recherchez l’extension, puis cliquez sur **désinstallation**.  
  
 Si pour une raison quelconque, aucune de ces méthodes aboutit à la désinstallation de l’extension, vous pouvez désinscrire l’assembly VSPackage à partir de la ligne de commande comme suit :  
  
```  
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\regpkg" /unregister <pathToVSPackage assembly>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Packages VS](../extensibility/internals/vspackages.md)
