---
title: Exécuter un test unitaire comme processus 64 bits
ms.date: 03/10/2020
ms.topic: how-to
helpviewer_keywords:
- unit tests, creating
- unit tests, running
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 3c5cb51232457a43200c8a71ace51cc4b8a63e02
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "88507984"
---
# <a name="run-a-unit-test-as-a-64-bit-process"></a>Exécuter un test unitaire comme processus 64 bits

Si vous avez un ordinateur 64 bits, vous pouvez exécuter des tests unitaires et capturer les informations de couverture du code en tant que processus 64 bits.

## <a name="to-run-a-unit-test-as-a-64-bit-process"></a>Pour exécuter un test unitaire en tant que processus 64 bits

1. Si votre code ou vos tests ont été compilés en tant que 32 bits/x86, mais que vous souhaitez maintenant les exécuter en tant que processus 64 bits, recompilez-les comme **n’importe quel processeur**.

   ::: moniker range="vs-2017"
   Dans Visual Studio 2017, vous pouvez également compiler votre projet sous la forme **64 bits**.
   ::: moniker-end

    > [!TIP]
    > Pour une flexibilité maximale, compilez vos projets de test avec la configuration **N’importe quelle UC**. Vous pouvez ensuite les exécuter sur des agents 32 bits et 64 bits. Il n’existe aucun avantage à compiler des projets de test avec la configuration **64 bits** , sauf si vous appelez du code qui est uniquement pris en charge sur 64 bits.

2. Définissez les tests unitaires pour qu’ils s’exécutent en tant que processus 64 bits.

   ::: moniker range=">=vs-2019"
   Dans le menu Visual Studio, choisissez **test**, puis **architecture de processeur pour les projets AnyCPU**. Choisissez **x64** pour exécuter les tests en tant que processus 64 bits.
   ::: moniker-end
   ::: moniker range="vs-2017"
   Dans le menu Visual Studio, choisissez **test**, paramètres de **test**, puis **architecture de processeur**. Choisissez **x64** pour exécuter les tests en tant que processus 64 bits.
   ::: moniker-end

   \- ou -

   Spécifiez `<TargetPlatform>x64</TargetPlatform>` dans un fichier *.runsettings*. Un avantage de cette méthode est que vous pouvez spécifier des groupes de paramètres dans des fichiers différents et changer rapidement de paramètres. Vous pouvez également copier des paramètres entre les solutions. Pour plus d’informations, consultez [Configurer des tests unitaires à l’aide d’un fichier .runsettings](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md).

## <a name="see-also"></a>Voir aussi

- [Exécuter des tests unitaires avec l'Explorateur de tests](../test/run-unit-tests-with-test-explorer.md)
- [Test unitaire de votre code](../test/unit-test-your-code.md)
