---
title: Inscription et la désinscription de VSPackages | Microsoft Docs
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
- registration, VSPackages
- VSPackages, registering
ms.assetid: e25e7a46-6a55-4726-8def-ca316f553d6b
caps.latest.revision: 36
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f5f43dd44dde41de4ecf3e34fa5e895ee0f4711f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49187614"
---
# <a name="registering-and-unregistering-vspackages"></a>Inscription et désinscription de VSPackages
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous utilisez des attributs pour inscrire un VSPackage, mais  
  
## <a name="registering-a-vspackage"></a>L’inscription d’un VSPackage  
 Vous pouvez utiliser des attributs pour contrôler l’inscription de VSPackages gérés. Toutes les informations d’inscription sont contenues dans un fichier .pkgdef. Pour plus d’informations sur le fichier d’inscription, consultez [utilitaire CreatePkgDef](../extensibility/internals/createpkgdef-utility.md).  
  
 Le code suivant montre comment utiliser les attributs standard d’inscription pour inscrire votre VSPackage.  
  
```csharp  
[PackageRegistration(UseManagedResourcesOnly = true)]  
[Guid("0B81D86C-0A85-4f30-9B26-DD2616447F95")]  
public sealed class BasicPackage : Package  
{. . .}  
```  
  
## <a name="unregistering-an-extension"></a>Annuler l’inscription d’une Extension  
 Si vous avez expérimenté, avec un grand nombre de VSPackages différents et que vous souhaitez les supprimer de l’instance expérimentale, vous pouvez exécuter la **réinitialiser** commande. Recherchez **réinitialiser l’Instance expérimentale de Visual Studio** sur la page de démarrage de votre ordinateur, ou exécutez cette commande à partir de la ligne de commande :  
  
```vb  
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe" /Reset /VSInstance=14.0 /RootSuffix=Exp  
```  
  
 Si vous souhaitez désinstaller une extension que vous avez installée sur votre instance de développement de Visual Studio, accédez à **outils / Extensions et mises à jour**, recherchez l’extension, puis cliquez sur **désinstallation**.  
  
 Si pour une raison quelconque, aucune de ces méthodes ne réussit à désinstaller l’extension, vous pouvez désinscrire l’assembly VSPackage à partir de la ligne de commande comme suit :  
  
```  
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\regpkg” /unregister <pathToVSPackage assembly>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [VSPackages](../extensibility/internals/vspackages.md)

