---
title: Exécuter un test unitaire comme processus 64 bits | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- unit tests, creating
- unit tests, running
ms.assetid: d23a9ee7-58e3-4e8b-a38c-b2207ea73fea
caps.latest.revision: 27
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fc379f522d119e76ef8be8ba60a4cc1482e57fd1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72660464"
---
# <a name="run-a-unit-test-as-a-64-bit-process"></a>Exécuter un test unitaire comme processus 64 bits
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Si vous avez un ordinateur 64 bits, vous pouvez exécuter des tests unitaires et capturer les informations de couverture du code en tant que processus 64 bits.

## <a name="running-a-unit-test-as-a-64-bit-process"></a>Exécution d’un test unitaire en tant que processus 64 bits

#### <a name="to-run-a-unit-test-as-a-64-bit-process"></a>Pour exécuter un test unitaire en tant que processus 64 bits

1. Si votre code ou vos tests ont été compilés en tant que 32-bit/x86, mais que vous souhaitez maintenant les exécuter en tant que processus 64 bits, vous devez les recompiler en tant qu’**Any CPU** ou éventuellement en tant que **64 bits**.

    > [!TIP]
    > Pour une flexibilité maximale, vous devez compiler vos projets de test avec la configuration **Any CPU**. Vous pouvez ensuite les exécuter sur des agents 32 et 64 bits. La compilation de projets de test avec la configuration **64 bits** ne présente aucun avantage particulier.

2. Dans le menu de Visual Studio, choisissez **Test**, puis **Paramètres** et enfin **Architecture de processeur**. Choisissez **x64** pour exécuter les tests en tant que processus 64 bits.

     \- ou -

     Spécifiez `<TargetPlatform>x64</TargetPlatform>` dans un fichier .runsettings. Un avantage de cette méthode est que vous pouvez spécifier des groupes de paramètres dans des fichiers différents et changer rapidement de paramètres. Vous pouvez également copier des paramètres entre les solutions. Pour plus d’informations, consultez [Configurer des tests unitaires à l’aide d’un fichier .runsettings](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md).

## <a name="see-also"></a>Voir aussi
 [Exécuter des tests unitaires avec l’Explorateur de tests](../test/run-unit-tests-with-test-explorer.md) [unité Testez votre code](../test/unit-test-your-code.md) [spécification des paramètres de test pour les tests Visual Studio](https://msdn.microsoft.com/library/0c15317e-80c6-4317-aed3-82b8e15e3901)
