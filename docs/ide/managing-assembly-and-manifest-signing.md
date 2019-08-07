---
title: Gérer la signature d’assemblys et de manifestes
ms.date: 02/17/2017
ms.technology: vs-ide-deployment
ms.topic: conceptual
helpviewer_keywords:
- manifests [Visual Studio]
- signing manifests [Visual Studio]
- application manifests [Visual Studio]
- assemblies [Visual Studio], signing
ms.assetid: 6c1ef36b-25f7-4ad0-b29a-51801b7a5420
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3add6e3e4f38b5ba73cd5154720d7b283189526e
ms.sourcegitcommit: 85d66dc9fea3fa49018263064876b15aeb6f9584
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68461498"
---
# <a name="manage-assembly-and-manifest-signing"></a>Gérer la signature d’assemblys et de manifestes

La signature avec un nom fort fournit à un composant logiciel une identité globalement unique. L’utilisation de noms forts garantit que l’assembly ne peut pas être usurpé et que les dépendances de composants et les instructions de configuration correspondent aux composant et version de composant appropriés.

Un nom fort est constitué de l’identité de l’assembly (simple nom textuel, numéro de version et informations de culture), ainsi que d’un jeton de clé publique et d’une signature numérique.

Pour plus d’informations sur la signature d’assemblys dans les projets Visual Basic et C#, consultez [Créer et utiliser des assemblys avec nom fort](/dotnet/framework/app-domains/create-and-use-strong-named-assemblies).

Pour plus d’informations sur la signature d’assemblys dans les projets Visual C++, consultez [Assemblys de nom fort (C++/CLI)](/cpp/dotnet/strong-name-assemblies-assembly-signing-cpp-cli).

> [!NOTE]
> La signature avec nom fort ne protège pas l’assembly contre l’ingénierie à rebours. Pour se protéger de l’ingénierie à rebours, consultez [Dotfuscator Community](dotfuscator/index.md).

## <a name="asset-types-and-signing"></a>Types de composants et signature

Vous pouvez signer les manifestes d’application et les assemblys .NET :

- Exécutables ( *.exe*)

- Manifestes d’application ( *.exe.manifest*)

- Manifestes de déploiement ( *.application*)

- Assemblys de composants partagés ( *.dll*)

Signez les types de composants suivants :

1. Assemblys, si vous souhaitez les déployer dans le Global Assembly Cache (GAC).

2. Manifestes d’application et de déploiement ClickOnce. Visual Studio permet la signature par défaut pour ces applications.

3. Assemblys PIA (Primary Interop Assembly), qui sont utilisés pour l’interopérabilité COM. L’utilitaire TLBIMP applique des noms forts pendant la création d’un assembly PIA à partir d’une bibliothèque de types COM.

En général, vous ne devez pas signer les exécutables. Un composant avec nom fort ne peut pas référencer un composant sans nom fort qui est déployé avec l’application. Visual Studio ne signe pas les exécutables d’application. En revanche, il signe le manifeste d’application, qui pointe vers l’exécutable portant un nom faible. Évitez de signer les composants qui appartiennent à votre application, car la signature peut rendre les dépendances plus difficiles à gérer.

## <a name="how-to-sign-an-assembly-in-visual-studio"></a>Guide pratique pour signer un assembly dans Visual Studio

Vous signez une application ou un composant à l’aide de l’onglet **Signature** de la fenêtre des propriétés du projet (cliquez avec le bouton droit sur le nœud de projet dans l’**Explorateur de solutions** et sélectionnez **Propriétés**). Sélectionnez l’onglet **Signature**, puis cochez la case **Signer l’assembly**.

Spécifiez un fichier de clé. Si vous choisissez de créer un fichier de clé, les fichiers de ce type sont toujours créés au format *.pfx*. Vous avez besoin d’un nom et d’un mot de passe pour le nouveau fichier.

> [!WARNING]
> Vous devez toujours protéger votre fichier de clé avec un mot de passe pour empêcher son utilisation par un tiers. Vous pouvez également sécuriser vos clés à l’aide des fournisseurs ou des magasins de certificats.

Vous pouvez également pointer vers une clé que vous avez déjà créée. Pour plus d’informations sur la création de clés, consultez [Créer une paire de clés publique/privée](/dotnet/framework/app-domains/how-to-create-a-public-private-key-pair).

Si vous avez accès uniquement à une clé publique, vous pouvez utiliser la signature différée pour reporter l’assignation de la clé. Vous activez la signature différée en cochant la case **Différer la signature uniquement**. Un projet à signature différée ne s’exécute pas, et vous ne pouvez pas le déboguer. Toutefois, vous pouvez ignorer la vérification pendant le développement à l’aide de l’option `-Vr` de [l’outil Sn.exe (Strong Name Tool)](/dotnet/framework/tools/sn-exe-strong-name-tool).

Pour plus d’informations sur la signature des manifestes, consultez [Guide pratique pour signer des manifestes d’application et de déploiement](../ide/how-to-sign-application-and-deployment-manifests.md).

## <a name="see-also"></a>Voir aussi

- [Assemblys avec nom fort](/dotnet/framework/app-domains/strong-named-assemblies)
- [Assemblys avec nom fort (C++/CLI)](/cpp/dotnet/strong-name-assemblies-assembly-signing-cpp-cli)
