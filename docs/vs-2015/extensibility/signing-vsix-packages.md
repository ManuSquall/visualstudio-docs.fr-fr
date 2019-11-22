---
title: Signature des packages VSIX | Microsoft Docs
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
ms.openlocfilehash: b74222804e9ed42e6f8263cbe6ad0daf19cda81f
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300327"
---
# <a name="signing-vsix-packages"></a>Signature de packages VSIX
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Les assemblys d’extension n’ont pas besoin d’être signés pour pouvoir s’exécuter dans Visual Studio, mais il est conseillé de le faire.  
  
 Si vous souhaitez sécuriser votre extension et vérifier qu’elle n’a pas été falsifiée, vous pouvez ajouter une signature numérique à un package VSIX. Lorsqu’un VSIX est signé, le programme d’installation VSIX affiche un message indiquant qu’il est signé, ainsi que des informations supplémentaires sur la signature elle-même. Si le contenu de l’extension VSIX a été modifié et que le VSIX n’a pas été signé à nouveau, le programme d’installation VSIX indique que la signature n’est pas valide. L’installation n’est pas arrêtée, mais l’utilisateur reçoit un avertissement.  
  
> [!IMPORTANT]
> À compter de 2015, les packages VSIX signés à l’aide de tout autre que le chiffrement SHA256 seront identifiés comme ayant une signature non valide. L’installation de VSIX n’est pas bloquée, mais l’utilisateur reçoit un avertissement.  
  
## <a name="signing-a-vsix-with-vsixsigntool"></a>Signature d’un VSIX avec VSIXSignTool  
 Un outil de signature de chiffrement SHA256 est disponible à partir de [VisualStudioExtensibility](https://www.nuget.org/profiles/VisualStudioExtensibility) sur NuGet.org sur [VsixSignTool](https://www.nuget.org/packages/Microsoft.VSSDK.Vsixsigntool).  
  
#### <a name="to-use-the-vsixsigntool"></a>Pour utiliser VSIXSignTool  
  
1. Ajoutez votre extension VSIX à un projet.  
  
2. Cliquez avec le bouton droit sur le nœud du projet dans Explorateur de solutions, en sélectionnant **ajouter &#124; gérer les packages NuGet**.  Pour plus d’informations sur NuGet et l’ajout de packages NuGet, consultez [vue d’ensemble de NuGet](https://docs.microsoft.com/nuget/) et [gérer les packages NuGet à l’aide de la boîte de dialogue](https://docs.microsoft.com/nuget/consume-packages/install-use-packages-visual-studio).  
  
3. Recherchez VSIXSignTool à partir de VisualStudioExtensibility et installez le package NuGet.  
  
4. Vous pouvez maintenant exécuter le VSIXSignTool à partir de l’emplacement des packages locaux du projet. Consultez l’aide de la ligne de commande de l’outil pour votre scénario de signature (VSIXSignTool. exe/ ?).  
  
   Par exemple, pour vous connecter avec un fichier de certificat protégé par mot de passe :  
  
   VSIXSignTool. exe Sign/f \<CertFile >/p \<mot de passe > \<VSIXfile >  
  
## <a name="see-also"></a>Voir aussi  
 [Publication d’extensions Visual Studio](../extensibility/shipping-visual-studio-extensions.md)
