---
title: Modification de feuilles de style XSLT
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: 080bed0f-0ca9-4be7-aecd-6bdaebc04007
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8a8625defb0d9e8d656aac7bb3d2236d4f5bb9c9
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55021882"
---
# <a name="edit-xslt-style-sheets"></a>Modification des feuilles de style XSLT

L'Éditeur XML permet également de modifier des feuilles de style XSLT. Vous pouvez ainsi tirer profit des fonctionnalités par défaut de l'éditeur telles qu'IntelliSense, mode plan, extraits XML, etc. Des nouvelles fonctions facilitent en outre le développement en XSLT.

## <a name="xslt-features"></a>Fonctions XSLT
 Le tableau suivant décrit les fonctionnalités spécifiques à la manipulation des feuilles de style XSLT.

 **La coloration syntaxique**

 Mots clés XSLT, tels que `template`, `match`, et ainsi de suite, sont affichés dans la couleur de mot clé XSLT spécifiée par le **polices et couleurs** paramètres.

 **Soulignements ondulés**

 L’éditeur XML utilise installée *xslt.xsd* fichier pour valider les feuilles de style XSLT. Les erreurs de validation sont indiquées par des soulignements ondulés bleus. L'éditeur XML compile également la feuille de style en arrière-plan et signale les erreurs ou avertissements du compilateur à l'aide de soulignements ondulés appropriés.

 **Prise en charge des blocs de script**

 Le code placé dans des blocs de script est pris en charge par le débogueur XSLT ; vous pouvez donc définir des points d'arrêt et effectuer une exécution pas à pas dans le code du bloc de script.

 **Afficher la sortie XSLT**

 Vous pouvez exécuter une transformation XSL et afficher la sortie depuis l'éditeur XML. Pour plus d'informations, voir [Procédure : Exécuter une transformation XSLT à partir de l’éditeur XML](../xml-tools/how-to-execute-an-xslt-transformation-from-the-xml-editor.md).

 **Débogage XSLT**

 Vous pouvez lancer le débogueur XSLT à partir d'un fichier XSLT dans l'éditeur XML. Le débogueur prend en charge la définition de points d'arrêt dans le fichier XSLT, l'affichage de l'état d'exécution de XSLT, etc. Lorsque le pointeur est placé sur une variable XSLT, une info-bulle apparaît et affiche la valeur de la variable. Le débogueur peut permettre de déboguer une feuille de style ou une transformation XSLT compilée invoquée depuis une autre application. Pour plus d’informations, consultez [XSLT débogage](../xml-tools/debugging-xslt.md).

## <a name="see-also"></a>Voir aussi

- [Éditeur XML](../xml-tools/xml-editor.md)