---
title: Signature de Packages VSIX | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- signature
- signing
- authenticode
- vsix
- packages
ms.assetid: e34cfc2c-361c-44f8-9cfe-9f2be229d248
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9fabe2931310b97f0c0864ea77ceef024f0e57cd
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63447205"
---
# <a name="signing-vsix-packages"></a>Signature de packages VSIX
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Assemblys d’extension n’avez pas besoin être signés avant qu’ils peuvent s’exécuter dans Visual Studio, mais il est conseillé de le faire.  
  
 Si vous souhaitez sécuriser votre extension et assurez-vous qu’il n’a pas été falsifié, vous pouvez ajouter une signature numérique à un package VSIX. Lorsqu’une extension VSIX est signée, le programme d’installation VSIX affichera un message indiquant qu’il est signé, ainsi que de plus d’informations sur la signature proprement dite. Si le contenu de l’extension VSIX a été modifié, et l’extension VSIX n’a pas été signé à nouveau, le programme d’installation VSIX affichera que la signature n’est pas valide. L’installation n’est pas arrêtée, mais l’utilisateur est averti.  
  
> [!IMPORTANT]
> À compter de 2015, les packages VSIX signés à l’aide d’autre que le chiffrement SHA256 seront identifiés comme ayant une signature non valide. Installation de VSIX n’est pas bloquée, mais l’utilisateur est averti.  
  
## <a name="signing-a-vsix-with-vsixsigntool"></a>Signature d’une extension VSIX avec VSIXSignTool  
 Il existe un chiffrement SHA256 outil disponible à partir de la signature [VisualStudioExtensibility](http://www.nuget.org/profiles/VisualStudioExtensibility) sur nuget.org à [VsixSignTool](http://www.nuget.org/packages/Microsoft.VSSDK.Vsixsigntool).  
  
#### <a name="to-use-the-vsixsigntool"></a>Pour utiliser le VSIXSignTool  
  
1. Ajouter votre projet VSIX à un projet.  
  
2. Cliquez avec le bouton droit sur le nœud de projet dans l’Explorateur de solutions, en sélectionnant **ajouter &#124; gérer les Packages NuGet**.  Pour plus d’informations sur NuGet et l’ajout de NuGet packages consultez [vue d’ensemble de NuGet](http://docs.nuget.org/) et [gérer NuGet Packages à l’aide de la boîte de dialogue](http://docs.nuget.org/Consume/Package-Manager-Dialog).  
  
3. Recherchez VSIXSignTool à partir de VisualStudioExtensibility et installez le package NuGet.  
  
4. Vous pouvez maintenant exécuter le VSIXSignTool à partir de l’emplacement du projet lots locaux. Consultez l’aide de la ligne de commande de l’outil pour votre scénario de signature (VSIXSignTool.exe / ?).  
  
   Par exemple, pour vous connecter avec un fichier de certificat protégé par mot de passe :  
  
   VSIXSignTool.exe sign /f \<certfile> /p \<password> \<VSIXfile>  
  
## <a name="see-also"></a>Voir aussi  
 [Publication d’extensions Visual Studio](../extensibility/shipping-visual-studio-extensions.md)
