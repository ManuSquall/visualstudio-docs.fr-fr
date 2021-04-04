---
title: Migrer testsettings vers RunSettings
description: Découvrez comment migrer testsettings vers RunSettings
ms.custom: SEO-VS-2020
ms.date: 03/18/2021
ms.topic: conceptual
f1_keywords:
- vs.UnitTest.Migrate
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ab1cfe921777fa75d4f69251668934e8d78d9bec
ms.sourcegitcommit: 155d5f0fd54ac1d20df2f5b0245365924faa3565
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/31/2021
ms.locfileid: "106087185"
---
# <a name="upgrade-from--testsettings-to-runsettings"></a>Mise à niveau de  *. testsettings* vers *. RunSettings*

Vous pouvez mettre à niveau votre fichier de configuration de test à partir de *. testsettings* vers *. RunSettings* à l’aide de l’outil SettingsMigrator qui est installé avec Visual Studio. En fonction de l’emplacement d’installation de Visual Studio, vous trouverez l’outil de migration des paramètres dans le chemin d’accès suivant : `C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise\Common7\IDE\Extensions\TestPlatform\SettingsMigrator.exe`

Dans l’emplacement de répertoire correct, vous pouvez exécuter l’outil avec le format ci-dessous :

```console
SettingsMigrator.exe <Full path to testsettings file to be migrated>
SettingsMigrator.exe <Full path to testsettings file to be migrated> <Full path to runsettings file to be created>
```

## <a name="examples"></a>Exemples
```console
SettingsMigrator.exe E:\MyTest\MyTestSettings.testsettings
SettingsMigrator.exe E:\MyTest\MyTestSettings.testsettings E:\MyTest\MyNewRunSettings.runsettings
```

Si vous souhaitez en savoir plus sur la façon dont les options *. testsettings* sont converties en *. RunSettings* , vous trouverez plus d’informations sur l’implémentation dans le [référentiel de plateforme de test Open source](https://github.com/microsoft/vstest-docs/blob/master/RFCs/0023-TestSettings-Deprecation.md#migration) sur GitHub.

## <a name="see-also"></a>Voir aussi

- [Configurer des séries de tests avec `.runsettings`](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)
- [Mise à niveau de MSTestv1 vers MSTestv2](../test/mstest-update-to-mstestv2.md)
- [Test unitaire de votre code](../test/unit-test-your-code.md)
- [Déboguer des tests unitaires avec l’Explorateur de tests](../test/debug-unit-tests-with-test-explorer.md)
