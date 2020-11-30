---
title: Spécifier le nombre d’itérations dans le paramètre d’exécution du test de charge
description: Découvrez comment spécifier le nombre d’itérations à exécuter sur tous les tests unitaires et de performances de site Web dans tous les scénarios d’un test de charge à l’aide de l’éditeur de test de charge.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, properties
- load tests, run settings
ms.assetid: 45a625db-b3e7-4d64-beda-b9a76248096d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 754a5ad7612f6abbea52ea9d4bb4cb1d159f6dac
ms.sourcegitcommit: 9ce13a961719afbb389fa033fbb1a93bea814aae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/30/2020
ms.locfileid: "96328299"
---
# <a name="how-to-specify-the-number-of-test-iterations-in-a-load-test-run-setting"></a>Guide pratique pour spécifier le nombre d’itérations de tests dans un paramètre de test de charge

Après avoir créé votre test de charge avec l’**Assistant Nouveau test de charge**, vous pouvez utiliser l’**éditeur de test de charge** pour changer les propriétés des scénarios en fonction de vos besoins et objectifs. Pour plus d’informations, consultez [Procédure pas à pas : création et exécution d’un test de charge](../test/walkthrough-create-and-run-a-load-test.md).

À l’aide de l' **éditeur de test de charge**, vous pouvez modifier la propriété **itérations de test** d’une valeur de paramètres d’exécution dans la fenêtre **Propriétés** . La propriété **itérations de tests** spécifie le nombre d’itérations à exécuter sur tous les tests unitaires et de performances de site Web dans tous les scénarios d’un test de charge à l’aide de l' **éditeur de test de charge**.

> [!NOTE]
> Pour obtenir la liste complète des propriétés des paramètres d’exécution et leurs descriptions, consultez [Propriétés des paramètres d’exécution du test de charge](../test/load-test-run-settings-properties.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-specify-the-number-of-test-iterations-in-a-run-setting"></a>Pour indiquer le nombre d'itérations de test dans un paramètre d'exécution

1. Ouvrez un test de charge.

     L’**éditeur de test de charge** apparaît et affiche l’arborescence du test de charge.

2. Dans l’arborescence du test de charge, dans le dossier **Paramètres d’exécution**, choisissez un paramètre d’exécution.

3. Dans le menu **Affichage**, sélectionnez **Fenêtre Propriétés** pour afficher les catégories et propriétés du paramètre d’exécution de test de charge.

4. Affectez à la propriété **Utiliser les itérations des tests** la valeur **True**.

5. Dans la propriété **Itérations de tests**, entrez une valeur indiquant le nombre d’itérations de tests à exécuter durant le test de charge.

6. Après avoir changé la propriété, choisissez **Enregistrer** dans le menu **Fichier**. Vous pouvez exécuter ensuite votre test de charge à l’aide de la nouvelle valeur associée à **Itérations de tests**.

## <a name="see-also"></a>Voir aussi

- [Configurer les paramètres d’exécution des tests de charge](../test/configure-load-test-run-settings.md)
- [Propriétés des scénarios de test de charge](../test/load-test-scenario-properties.md)
