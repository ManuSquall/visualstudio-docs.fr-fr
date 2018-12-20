---
title: Exécuter un test unitaire comme processus 64 bits
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- unit tests, creating
- unit tests, running
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 4ee070adba33328253d7abeb122ec2ca2da145ef
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53062714"
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
