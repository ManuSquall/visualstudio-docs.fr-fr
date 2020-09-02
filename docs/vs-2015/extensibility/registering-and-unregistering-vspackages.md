---
title: Inscription et annulation de l’inscription de VSPackages | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- registration, VSPackages
- VSPackages, registering
ms.assetid: e25e7a46-6a55-4726-8def-ca316f553d6b
caps.latest.revision: 36
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1f6bc85fb00c15831dcf1a9f64e4b886272df218
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68193818"
---
# <a name="registering-and-unregistering-vspackages"></a>Inscription et désinscription de VSPackages
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous utilisez des attributs pour inscrire un VSPackage, mais  
  
## <a name="registering-a-vspackage"></a>Inscription d’un VSPackage  
 Vous pouvez utiliser des attributs pour contrôler l’inscription des VSPackages managés. Toutes les informations d’inscription sont contenues dans un fichier. pkgdef. Pour plus d’informations sur l’inscription basée sur les fichiers, consultez [CreatePkgDef Utility](../extensibility/internals/createpkgdef-utility.md).  
  
 Le code suivant montre comment utiliser les attributs d’inscription standard pour inscrire votre VSPackage.  
  
```csharp  
[PackageRegistration(UseManagedResourcesOnly = true)]  
[Guid("0B81D86C-0A85-4f30-9B26-DD2616447F95")]  
public sealed class BasicPackage : Package  
{. . .}  
```  
  
## <a name="unregistering-an-extension"></a>Annulation de l’inscription d’une extension  
 Si vous avez fait des essais avec un grand nombre de VSPackages et souhaitez les supprimer de l’instance expérimentale, vous pouvez simplement exécuter la commande de **réinitialisation** . Recherchez **Réinitialiser l’instance expérimentale de Visual Studio** sur la page de démarrage de votre ordinateur, ou exécutez la commande suivante à partir de la ligne de commande :  
  
```vb  
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe" /Reset /VSInstance=14.0 /RootSuffix=Exp  
```  
  
 Si vous souhaitez désinstaller une extension que vous avez installée sur votre instance de développement de Visual Studio, accédez à **Outils/extensions et mises à jour**, recherchez l’extension, puis cliquez sur **désinstaller**.  
  
 Si, pour une raison quelconque, aucune de ces méthodes ne parvient à désinstaller l’extension, vous pouvez annuler l’inscription de l’assembly VSPackage à partir de la ligne de commande comme suit :  
  
```  
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\regpkg” /unregister <pathToVSPackage assembly>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [VSPackages](../extensibility/internals/vspackages.md)
