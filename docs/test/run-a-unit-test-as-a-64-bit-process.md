---
title: Exécuter un test unitaire comme processus 64 bits
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- unit tests, creating
- unit tests, running
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: cd4cf41906fc9c8d4b5fbce407f1910d5e972dee
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62945745"
---
# <a name="run-a-unit-test-as-a-64-bit-process"></a>Exécuter un test unitaire comme processus 64 bits

Si vous avez un ordinateur 64 bits, vous pouvez exécuter des tests unitaires et capturer les informations de couverture du code en tant que processus 64 bits.

## <a name="to-run-a-unit-test-as-a-64-bit-process"></a>Pour exécuter un test unitaire en tant que processus 64 bits

1. Si votre code ou vos tests ont été compilés en tant que 32-bit/x86, mais que vous souhaitez maintenant les exécuter en tant que processus 64 bits, vous devez les recompiler en tant qu’**Any CPU** ou éventuellement en tant que **64 bits**.

    > [!TIP]
    > Pour une flexibilité maximale, compilez vos projets de test avec la configuration **N’importe quelle UC**. Vous pouvez ensuite les exécuter sur des agents 32 bits et 64 bits. La compilation de projets de test avec la configuration **64 bits** ne présente aucun avantage particulier.

2. Dans le menu de Visual Studio, choisissez **Test**, puis **Paramètres** et enfin **Architecture de processeur**. Choisissez **x64** pour exécuter les tests en tant que processus 64 bits.

   - ou

   Spécifiez `<TargetPlatform>x64</TargetPlatform>` dans un fichier *.runsettings*. Un avantage de cette méthode est que vous pouvez spécifier des groupes de paramètres dans des fichiers différents et changer rapidement de paramètres. Vous pouvez également copier des paramètres entre les solutions. Pour plus d’informations, consultez [Configurer des tests unitaires à l’aide d’un fichier .runsettings](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md).

## <a name="see-also"></a>Voir aussi

- [Exécuter des tests unitaires avec l’Explorateur de tests](../test/run-unit-tests-with-test-explorer.md)
- [Tests unitaires sur votre code](../test/unit-test-your-code.md)
