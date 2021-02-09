---
title: Fonctionnalités IntelliSense de l’éditeur XML
description: Découvrez les fonctionnalités IntelliSense de l’éditeur XML dans Visual Studio et comment les utiliser avec des documents en langage XSD (XML Schema Definition) et XSLT.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 2b26f214-cc3a-46bf-b260-14eb8e599182
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 330dbdfb6d6db8d33a2b8ea3caa7e1a840d84dd0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99874897"
---
# <a name="xml-editor-intellisense-features"></a>Fonctionnalités IntelliSense de l’éditeur XML

L'éditeur XML offre des fonctionnalités IntelliSense complètes comparables à celles d'autres éditeurs de langage fournis dans Visual Studio. Cette section explique comment vous pouvez utiliser IntelliSense avec des documents en langage XSD (XML Schema Definition) et XSLT.

## <a name="intellisense-in-an-xsd-document"></a>IntelliSense dans un document XSD

Une fois qu’un schéma est associé à votre document, vous recevez une liste déroulante d’éléments attendus chaque fois que vous tapez ou que vous `"<"` cliquez sur le bouton **afficher la liste des membres** de l’objet dans la barre d’outils de l’éditeur XML.

![Bouton afficher la liste des membres de l’objet](media/display-object-member-list-xml.png)

Pour plus d’informations sur la façon d’associer des schémas à vos documents XML, consultez [validation de document XML](../xml-tools/xml-document-validation.md).

Lorsque vous entrez un ESPACE dans une étiquette de début, vous obtenez également une liste déroulante de tous les attributs qui peuvent être ajoutés à l’élément actuel.

Lorsque vous entrez `"="` pour une valeur d'attribut ou que vous insérez le guillemet ouvrant introduisant cette valeur, vous obtenez également une liste des valeurs possibles pour cet attribut. Des valeurs ne sont proposées que lorsque le schéma fournit une énumération de valeurs via des facettes `xsd:enumeration` ou que l'attribut est de type `Boolean`. Une liste IntelliSense de codes de langage connus est également fournie pour `xml:lang` ou pour tout `simpleType` dérivant de `xsd:language`. Une liste IntelliSense des valeurs `targetNamespace` connues est fournie pour les déclarations d'espaces de noms.

Une liste IntelliSense des valeurs possibles est également fournie lorsque vous entrez `">"` pour fermer une balise de début si l'élément est de type `simpleType`. Le comportement des éléments est similaire à celui des attributs décrits dans le paragraphe précédent.

Des info-bulles s'affichent également dans les listes IntelliSense, d'après les informations `xsd:annotation` et `xsd:documentation` trouvées dans le schéma associé.

## <a name="intellisense-in-an-xslt-document"></a>IntelliSense dans un document XSLT

Après avoir ajouté un modèle nommé ou un attribut à votre document XSLT, vous pouvez utiliser IntelliSense pour insérer les éléments suivants :

- Noms d'ensemble d'attributs.

- Modes de modèle.

- Noms de modèle.

- Noms de paramètre pour un mode donné.

- Noms de paramètre pour un modèle nommé donné.

Pour plus d’informations, consultez la rubrique [procédure pas à pas : utilisation d’INTELLISENSE XSLT](../xml-tools/walkthrough-using-xslt-intellisense.md) .

## <a name="auto-completion"></a>Saisie semi-automatique

L'éditeur XML facilite également l'édition du XML en complétant automatiquement la syntaxe XML requise. Par exemple, si vous entrez l’étiquette de début suivante :

`<book>`

L’éditeur XML insère l’étiquette de fin et place le curseur juste après l’étiquette de début. Voici un exemple (le « &#124; » note la position du curseur) :

`<book>`&#124;`</book>`

Étant donné que les valeurs des attributs doivent toujours être placées entre guillemets, l'éditeur XML insère automatiquement ces guillemets. Par exemple, si vous entrez :

`<book title=`

L'éditeur XML ajoute les guillemets et place le curseur entre ces guillemets :

`<book title="`&#124;`"`

De même, l'éditeur XML insère automatiquement la syntaxe XML suivante :

- Fin d'une instruction de traitement : `?>`

- Fin d'un bloc CDATA : `]]>`

- Fin d'un commentaire : `-->`

- Fin d'une déclaration DTD : `>`

L’éditeur XML a également la possibilité d’insérer une déclaration d’espace de noms si vous sélectionnez un attribut ou un élément qualifié d’espace de noms dans une liste IntelliSense et que l’espace de noms de cet élément ou attribut n’est pas encore dans la portée.

Par exemple, si vous sélectionnez l'élément `e:Book` dans la liste IntelliSense, sachant que le préfixe est lié à l'espace de noms `http://books` qui n'a pas encore été déclaré dans le document, l'éditeur XML insère automatiquement la déclaration d'espace de noms requise. Il en résulte le texte XML suivant :

`<e:Book xmlns:e="http://books"`

## <a name="brace-matching"></a>Correspondance d’accolade

L'éditeur XML met en évidence les accolades pour indiquer immédiatement quel élément vous venez de fermer. Vous pouvez également utiliser le raccourci clavier (**CTRL** + **]**) pour passer d’une accolade à l’accolade correspondante.

L'éditeur XML offre cette fonctionnalité pour les éléments suivants :

- Correspondance des balises de début et de fin.

- Toute paire de crochets pointus « \<" or "> ».

- Début et fin des commentaires.

- Début et fin des instructions de traitement.

- Début et fin des blocs CDATA.

- Début et fin des déclarations DTD.

- Ouverture et fermeture des guillemets sur les attributs.

## <a name="modify-the-intellisense-options"></a>Modifier les options IntelliSense

Les fonctions IntelliSense et de saisie semi-automatique sont activées par défaut. Toutefois, vous pouvez modifier ce paramètre en modifiant les   >  paramètres **options** des outils.

La section **insertion automatique** de la page **divers** contrôle le comportement suivant :

|Nom|Description|
|-|-----------------|
|Balises de fermeture|Insère des étiquettes de fermeture pour les nouveaux éléments.|
|Guillemets d'attribut|Insère les guillemets marquant une valeur d'attribut lorsque vous entrez un nouveau nom d'attribut.|
|Autre balisage|Complète les commentaires, CDATA, DOCTYPE, instructions de traitement et autres déclarations de balisage.|

### <a name="to-change-the-auto-completion-behavior"></a>Pour modifier le comportement de la saisie semi-automatique

1. Sélectionnez **Options** dans le menu **Outils**.

2. Développez **éditeur de texte**, développez **XML**, puis sélectionnez **divers**.

3. Apportez des modifications à la section **insertion automatique** , puis cliquez sur **OK**.

## <a name="see-also"></a>Voir aussi

- [Éditeur XML](../xml-tools/xml-editor.md)
- [Utilisation d’IntelliSense](../ide/using-intellisense.md)
- [Procédure pas à pas : utilisation d’IntelliSense XSLT](../xml-tools/walkthrough-using-xslt-intellisense.md)
