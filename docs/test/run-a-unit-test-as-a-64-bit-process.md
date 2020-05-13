---
title: Exécuter un test unitaire comme processus 64 bits
ms.date: 03/10/2020
ms.topic: conceptual
helpviewer_keywords:
- unit tests, creating
- unit tests, running
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: d6c6839f8c4702d88d1022116231c6f22b5dbf21
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79093905"
---
# <a name="run-a-unit-test-as-a-64-bit-process"></a>Exécuter un test unitaire comme processus 64 bits

Si vous avez un ordinateur 64 bits, vous pouvez exécuter des tests unitaires et capturer les informations de couverture du code en tant que processus 64 bits.

## <a name="to-run-a-unit-test-as-a-64-bit-process"></a>Pour exécuter un test unitaire en tant que processus 64 bits

1. Si votre code ou tests ont été compilés comme 32 bits/x86, mais vous voulez maintenant les exécuter comme un processus 64 bits, recompliquez-les comme **N’importe quel processeur**.

   ::: moniker range="vs-2017"
   Alternativement, Dans Visual Studio 2017, vous pouvez également compiler votre projet en **64 bits**.
   ::: moniker-end

    > [!TIP]
    > Pour une flexibilité maximale, compilez vos projets de test avec la configuration **N’importe quelle UC**. Vous pouvez ensuite les exécuter sur des agents 32 bits et 64 bits. La compilation de projets de test avec la configuration **64 bits** ne présente aucun avantage particulier.

2. Définissez les tests unitaires pour qu’ils s’exécutent comme un processus 64 bits.

   ::: moniker range=">=vs-2019"
   Dans le menu Visual Studio, choisissez **Test**, puis choisissez **Processor Architecture pour les projets AnyCPU**. Choisissez **x64** pour exécuter les tests en tant que processus 64 bits.
   ::: moniker-end
   ::: moniker range="vs-2017"
   Dans le menu Visual Studio, choisissez **Test**, puis choisissez **Test Settings**, puis choisissez **Processor Architecture**. Choisissez **x64** pour exécuter les tests en tant que processus 64 bits.
   ::: moniker-end

   \- ou -

   Spécifiez `<TargetPlatform>x64</TargetPlatform>` dans un fichier *.runsettings*. Un avantage de cette méthode est que vous pouvez spécifier des groupes de paramètres dans des fichiers différents et changer rapidement de paramètres. Vous pouvez également copier des paramètres entre les solutions. Pour plus d’informations, consultez [Configurer des tests unitaires à l’aide d’un fichier .runsettings](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md).

## <a name="see-also"></a>Voir aussi

- [Exécuter des tests unitaires avec Test Explorer](../test/run-unit-tests-with-test-explorer.md)
- [Test unitaire de votre code](../test/unit-test-your-code.md)
