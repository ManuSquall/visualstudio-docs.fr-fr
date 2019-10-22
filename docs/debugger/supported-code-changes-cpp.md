---
title: Modifications du code prisesC++en charge () | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Edit and Continue, limitations
- supported code changes
- object files, limitations of Edit and Continue
- C++ language, supported code changes
- coding, supported code changes
- resource files, limitations of Edit and Continue
- code changes, handling in Edit and Continue
- what's new [C++], supported code changes
- code changes
ms.assetid: f5754363-8a56-417b-b904-b05d9dd26d03
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 8e38123be6b780aa9f37dc2b329ec36e3f18e793
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72430572"
---
# <a name="supported-code-changes-c"></a>Modifications de code prises en charge (C++)
Modifier & Continuer pour C++ les projets gère la plupart des types de modifications de code. Toutefois, certaines modifications ne peuvent pas être appliquées pendant l'exécution du programme. Pour appliquer ces modifications, vous devez arrêter l'exécution et générer une nouvelle version du code.

 Pour plus d’informations sur l’utilisation de modifier & Continuer pour C++ dans Visual Studio, consultez [Modifier & Continuer (C++)](../debugger/edit-and-continue-visual-cpp.md) .

## <a name="BKMK_Unsupported_changes"></a> Modifications non prises en charge
 Les modifications C/C++ suivantes ne peuvent pas être appliquées pendant une session de débogage :

- La plupart des modifications apportées aux données globales ou statiques.

- Modifications apportées à des exécutables copiés depuis un autre ordinateur et non générés localement.

- Modifications apportées à un type de données qui affectent la disposition d'un objet, comme les données membres d'une classe.

- Ajout de plus de 64 Ko de nouveau code ou de nouvelles données.

- Ajout de variables qui nécessitent un constructeur à un point situé avant le pointeur d'instruction.

- Modifications qui affectent le code qui nécessite une initialisation d'exécution.

- Ajout de gestionnaires d'exceptions, dans certains cas.

- Modifications apportées aux fichiers de ressources.

- Modifications apportées au code de fichiers en lecture seule.

- Modifications apportées au code sans fichier PDB correspondant.

- Modifications apportées au code sans fichier objet.

  Si vous procédez à l'une de ces modifications puis essayez de l'appliquer, un message d'erreur ou d'avertissement apparaît dans la fenêtre **Sortie** .

- Modifier & Continuer ne met pas à jour les bibliothèques statiques. Si vous apportez une modification dans une bibliothèque statique, l'exécution continue avec l'ancienne version et aucun avertissement n'est émis.

## <a name="BKMK_Unsupported_scenarios"></a> Scénarios non pris en charge
 Modifier & Continuer pour C/C++ n'est pas disponible dans les scénarios de débogage suivants :

- Débogage des applications natives compilées avec [/zo (Améliorer le débogage optimisé)](/cpp/build/reference/zo-enhance-optimized-debugging)

- Dans les versions de Visual Studio antérieures à Visual Studio 2015 Update 1, débogage des applications ou des composants UWP. À compter de Visual Studio 2015 Update 1, vous pouvez utiliser modifier & continuer dans C++ les applications UWP et DirectX, car il prend désormais en charge le commutateur du compilateur `/ZI` avec le commutateur `/bigobj`. Vous pouvez également utiliser l’option Modifier &amp; Continuer avec des fichiers binaires compilés à l’aide du commutateur `/FASTLINK` .

- Débogage sur Windows 98.

- Débogage en mode mixte (natif/managé).

- Débogage JavaScript.

- Débogage SQL.

- Débogage d'un fichier dump.

- Modification de code après une exception non gérée, lorsque l'option **Dérouler la pile des appels sur les exceptions non gérées** n'est pas sélectionnée.

- Débogage d'une application à l'aide de la commande **Attacher à** au lieu d'exécuter l'application en choisissant **Démarrer** dans le menu **Déboguer** .

- Débogage de code optimisé.

- Débogage d'une version ancienne de votre code après l'échec de génération d'une nouvelle version en raison d'erreurs de build.

## <a name="BKMK_Linking_limitations"></a> Limitations des liens

### <a name="BKMK_Linker_options_that_disable_Edit_and_Continue"></a> Options de l'Éditeur de liens désactivant Modifier & Continuer
 Les options suivantes de l'Éditeur de liens désactivent Modifier & Continuer :

- Définir **/OPT:REF**, **/OPT:ICF**ou **/INCREMENTAL:NO** désactive Modifier &amp; Continuer avec l'avertissement suivant :

     LINK : avertissement LNK4075 : /EDITANDCONTINUE ignoré en raison de la spécification de

     spécification

- Définir **/ORDER**, **/RELEASE**ou **/FORCE** désactive Modifier &amp; Continuer avec l'avertissement suivant :

     LINK : avertissement LNK4075 : /INCREMENTAL ignoré en raison de la spécification de

     spécification

- Définir toute option empêchant la création d'un fichier de base de données de programme (.pdb) désactive Modifier & Continuer sans avertissement spécifique.

### <a name="BKMK_Auto_relinking_limitations"></a> Limitations de la réédition automatique de liens
 Par défaut, Modifier & Continuer recrée les liens de votre programme à la fin d'une session de débogage pour créer un exécutable à jour.

 Modifier & Continuer ne peut pas rétablir les liens de votre programme si vous effectuez le débogage à un endroit différent de la génération d'origine. Un message vous invite à effectuer une régénération manuelle.

 Modifier & Continuer ne régénère pas les bibliothèques statiques. Si vous apportez des modifications à une bibliothèque statique avec Modifier & Continuer, vous devrez manuellement régénérer la bibliothèque et rétablir les liens des applications qui l'utilisent.

 Modifier & Continuer n'appelle pas d'étapes de build personnalisée. Si votre programme utilise des étapes de build personnalisée, vous pouvez réaliser des régénérations manuelles afin que les étapes de build personnalisée puissent être appelées. Dans ce cas, vous pouvez désactiver la création d'un nouveau lien après Modifier & Continuer afin d'être certain d'être invité à régénérer manuellement.

 **Pour désactiver la ré-édition des liens après exécution de Modifier & Continuer**

1. Dans le menu **Déboguer** , choisissez **Options et paramètres**.

2. Dans la boîte de dialogue **Options** , sous le nœud **Débogage** , sélectionnez le nœud **Modifier &amp; Continuer** .

3. Désactivez la case à cocher **Reconstruire le code modifié après le débogage** .

## <a name="BKMK_Precompiled_Header_Limitations"></a> Limitations des en-têtes précompilés
 Par défaut, Modifier & Continuer charge et traite les en-têtes précompilés en arrière-plan pour accélérer le traitement des modifications du code. Le chargement d'en-têtes précompilés exige l'allocation de mémoire physique, ce qui peut poser un problème si vous exécutez la compilation sur un ordinateur pauvre en mémoire vive. Pour savoir si vous vous trouvez dans cette situation, vous pouvez utiliser le Gestionnaire des tâches de Windows afin d'évaluer la quantité de mémoire physique disponible pendant que vous déboguez. Si cette quantité est supérieure à la taille des en-têtes précompilés, l'opération Modifier & Continuer devrait se dérouler sans problème. Si elle est inférieure à la taille des en-têtes précompilés, vous pouvez empêcher l'opération Modifier & Continuer de charger ces en-têtes en arrière-plan.

 **Pour désactiver le chargement en arrière-plan d'en-têtes précompilés par Modifier & Continuer**

1. Dans le menu **Déboguer** , choisissez **Options et paramètres**.

2. Dans la boîte de dialogue **Options** , sous le nœud **Débogage** , sélectionnez le nœud **Modifier &amp; Continuer** .

3. Désactivez la case à cocher **Autoriser la précompilation** .

## <a name="BKMK_IDL_Attribute_Limitations"></a> Limitations des attributs IDL
 La fonction Modifier & Continuer ne régénère pas de fichiers de définition d'interface (IDL). Par conséquent, les modifications des attributs IDL ne seront pas reflétées pendant le débogage. Pour voir le résultat des modifications apportées aux attributs IDL, vous devez arrêter le débogage et régénérer votre application. Modifier & Continuer ne génère pas d'erreur ou d'avertissement lorsque des attributs IDL ont été modifiés. Pour plus d'informations, consultez [Attributs IDL](/cpp/windows/idl-attributes).

## <a name="see-also"></a>Voir aussi
- [Modifier & Continuer (C++)](../debugger/edit-and-continue-visual-cpp.md)