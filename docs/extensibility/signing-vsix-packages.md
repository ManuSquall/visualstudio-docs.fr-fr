---
title: Signature de forfaits VSIX (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- signature
- signing
- authenticode
- vsix
- packages
ms.assetid: e34cfc2c-361c-44f8-9cfe-9f2be229d248
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 17179c35496fc19322c5bb951f4d04bc28e5d7bc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700090"
---
# <a name="signing-vsix-packages"></a>Signature de packages VSIX
Les assemblages d’extension n’ont pas besoin d’être signés avant de pouvoir fonctionner en Studio Visuel, mais c’est une bonne pratique de le faire.

 Si vous souhaitez sécuriser votre extension et vous assurer qu’elle n’a pas été altérée, vous pouvez ajouter une signature numérique à un package VSIX. Lorsqu’un VSIX est signé, l’installateur VSIX affiche un message indiquant qu’il est signé, ainsi que plus d’informations sur la signature elle-même. Si le contenu du VSIX a été modifié et que le VSIX n’a pas été signé à nouveau, l’installateur VSIX montrera que la signature n’est pas valide. L’installation n’est pas arrêtée, mais l’utilisateur est averti.

> [!IMPORTANT]
> À partir de Visual Studio 2015, les paquets VSIX signés en utilisant autre chose que le chiffrement SHA256 seront identifiés comme ayant une signature invalide. L’installation VSIX n’est pas bloquée mais l’utilisateur sera averti.

## <a name="signing-a-vsix-with-vsixsigntool"></a>Signature d’un VSIX avec VSIXSignTool
 Il existe un outil de signature de cryptage SHA256 disponible à partir de [VisualStudioExtensibility](https://www.nuget.org/profiles/VisualStudioExtensibility) sur nuget.org à [VsixSignTool](https://www.nuget.org/packages/Microsoft.VSSDK.Vsixsigntool).

#### <a name="to-use-the-vsixsigntool"></a>Pour utiliser le VSIXSignTool

1. Ajoutez votre VSIX à un projet.

2. Cliquez à droite sur le nœud du projet dans Solution Explorer, en sélectionnant **Ajouter &#124; Gérer les forfaits NuGet**.  Pour plus d’informations sur NuGet et l’ajout de forfaits NuGet, consultez les sujets [de la documentation NuGet](/NuGet) et [de l’interface utilisateur de Package Manager.](/NuGet/Tools/Package-Manager-UI)

3. Recherchez VSIXSignTool de VisualStudioExtensibility et installez le paquet NuGet.

4. Vous pouvez maintenant exécuter le VSIXSignTool à partir de l’emplacement des forfaits locaux du projet. Consultez l’aide de la ligne de commande de l’outil pour votre scénario de signature (VSIXSignTool.exe /?).

   Par exemple, pour signer avec un fichier de certificat protégé par mot de passe :

   VSIXSignTool.exe signe \</f certfile> \</p mot \<de passe> VSIXfile>

## <a name="see-also"></a>Voir aussi
- [Publication d’extensions Visual Studio](../extensibility/shipping-visual-studio-extensions.md)
