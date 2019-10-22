---
title: Modification de feuilles de style XSLT
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 080bed0f-0ca9-4be7-aecd-6bdaebc04007
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7fc987f8362d5daf435b7e9de860cc13f16a1aaf
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72646056"
---
# <a name="edit-xslt-style-sheets"></a>Modification des feuilles de style XSLT

L’éditeur XML peut également être utilisé pour modifier des feuilles de style XSLT. Vous pouvez ainsi tirer profit des fonctionnalités par défaut de l’éditeur telles qu’IntelliSense, mode plan, extraits XML, etc. Des nouvelles fonctionnalités facilitent en outre le développement en XSLT.

## <a name="xslt-features"></a>Fonctionnalités XSLT

Le tableau suivant décrit les fonctions spécifiques à la manipulation des feuilles de style XSLT.

**Coloration de la syntaxe**

Les mots clés XSLT, tels que `template` et `match`, s’affichent dans la couleur de mot clé XSLT spécifiée par les paramètres des **polices et des couleurs** .

**Traits de soulignement ondulés**

L’éditeur XML utilise le fichier *XSLT. xsd* installé pour valider les feuilles de style XSLT. Les erreurs de validation sont indiquées par des soulignements ondulés bleus. L’éditeur XML compile également la feuille de style en arrière-plan et signale les erreurs ou avertissements du compilateur avec des soulignements ondulés appropriés.

**Prise en charge des blocs de script**

Le code placé dans des blocs de script est pris en charge par le débogueur XSLT ; vous pouvez donc définir des points d'arrêt et effectuer une exécution pas à pas dans le code du bloc de script.

**Afficher la sortie XSLT**

Vous pouvez exécuter une transformation XSL et afficher la sortie de l’éditeur XML. Pour plus d’informations, consultez [procédure : exécution d’une transformation XSLT à partir de l’éditeur XML](../xml-tools/how-to-execute-an-xslt-transformation-from-the-xml-editor.md).

**Déboguer XSLT**

Vous pouvez lancer le débogueur XSLT à partir d’un fichier XSLT dans l’éditeur XML. Le débogueur prend en charge la définition de points d'arrêt dans le fichier XSLT, l'affichage de l'état d'exécution de XSLT, etc. Lorsque le pointeur est placé sur une variable XSLT, une info-bulle apparaît et affiche la valeur de la variable. Le débogueur peut permettre de déboguer une feuille de style ou une transformation XSLT compilée invoquée depuis une autre application. Pour plus d’informations, consultez [débogage XSLT](../xml-tools/debugging-xslt.md).

## <a name="see-also"></a>Voir aussi

- [Éditeur XML](../xml-tools/xml-editor.md)