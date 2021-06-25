---
title: Signature des packages VSIX | Microsoft Docs
description: En savoir plus sur la signature des assemblys d’extension. Le programme d’installation VSIX affiche un message indiquant qu’un VSIX est signé et des informations sur la signature elle-même.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- signature
- signing
- authenticode
- vsix
- packages
ms.assetid: e34cfc2c-361c-44f8-9cfe-9f2be229d248
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d481c75754c7bc49369987d4bf6dc3aa33e96fdc
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899158"
---
# <a name="signing-vsix-packages"></a>Signature de packages VSIX
Les assemblys d’extension n’ont pas besoin d’être signés pour pouvoir s’exécuter dans Visual Studio, mais il est conseillé de le faire.

 Si vous souhaitez sécuriser votre extension et vérifier qu’elle n’a pas été falsifiée, vous pouvez ajouter une signature numérique à un package VSIX. Lorsqu’un VSIX est signé, le programme d’installation VSIX affiche un message indiquant qu’il est signé, ainsi que des informations supplémentaires sur la signature elle-même. Si le contenu de l’extension VSIX a été modifié et que le VSIX n’a pas été signé à nouveau, le programme d’installation VSIX indique que la signature n’est pas valide. L’installation n’est pas arrêtée, mais l’utilisateur reçoit un avertissement.

> [!IMPORTANT]
> À compter de Visual Studio 2015, les packages VSIX signés à l’aide de tout autre que le chiffrement SHA256 seront identifiés comme ayant une signature non valide. L’installation de VSIX n’est pas bloquée, mais l’utilisateur reçoit un avertissement.

## <a name="signing-a-vsix-with-vsixsigntool"></a>Signature d’un VSIX avec VSIXSignTool
 Un outil de signature de chiffrement SHA256 est disponible à partir de [VisualStudioExtensibility](https://www.nuget.org/profiles/VisualStudioExtensibility) sur NuGet.org sur [VsixSignTool](https://www.nuget.org/packages/Microsoft.VSSDK.Vsixsigntool).

#### <a name="to-use-the-vsixsigntool"></a>Pour utiliser VSIXSignTool

1. Ajoutez votre extension VSIX à un projet.

2. Cliquez avec le bouton droit sur le nœud du projet dans Explorateur de solutions, en sélectionnant **ajouter &#124; gérer les packages NuGet**.  Pour plus d’informations sur NuGet et l’ajout de packages NuGet, consultez la [documentation NuGet](/NuGet) et les rubriques de l' [interface utilisateur du gestionnaire de package](/NuGet/Tools/Package-Manager-UI) .

3. Recherchez VSIXSignTool à partir de VisualStudioExtensibility et installez le package NuGet.

4. Vous pouvez maintenant exécuter le VSIXSignTool à partir de l’emplacement des packages locaux du projet. Consultez l’aide de la ligne de commande de l’outil pour votre scénario de signature (VSIXSignTool.exe/ ?).

   Par exemple, pour vous connecter avec un fichier de certificat protégé par mot de passe :

   VSIXSignTool.exe la signature/f \<certfile> /p \<password>\<VSIXfile>

## <a name="see-also"></a>Voir aussi
- [Publication d’extensions Visual Studio](../extensibility/shipping-visual-studio-extensions.md)
