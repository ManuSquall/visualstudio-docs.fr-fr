---
title: Interfaces Windows Script | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4c750627-6797-4857-9f5e-e5f54371f83c
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f98e60a82735ae561edf404763e0700f71b3a3d4
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49905361"
---
# <a name="windows-script-interfaces"></a>Windows Script, interfaces

Les interfaces Microsoft Windows Script permettent à une application d’ajouter des scripts et l’automation OLE. Les hôtes de script qui s’appuient sur Windows Script peuvent utiliser des moteurs de script provenant de plusieurs sources et fournisseurs pour gérer l’écriture des scripts entre les composants. L’implémentation du script proprement dit (langage, syntaxe, format persistant, modèle d’exécution et ainsi de suite) incombe à l’éditeur de script.

La documentation de Windows Script comporte les sections suivantes :

[Hôtes de script Windows](../winscript/windows-script-hosts.md)

[Moteurs de script Windows](../winscript/windows-script-engines.md)

[Présentation du débogage de script actif](../winscript/active-script-debugging-overview.md)

[Présentation du profilage de script actif](../winscript/active-script-profiling-overview.md)

[Référence d’interfaces de script Windows](../winscript/reference/windows-script-interfaces-reference.md)

## <a name="windows-script-background"></a>Informations générales sur Windows Script

Les interfaces Windows Script se répartissent en deux catégories : les moteurs Windows Script et les hôtes Windows Script. Un hôte crée un moteur de script et appelle le moteur pour exécuter les scripts. Voici quelques exemples d’hôtes Windows Script :

- Microsoft Internet Explorer

- Outils de création Internet

- Shell

Les moteurs Windows Script peuvent être développés pour tout langage ou environnement d’exécution, notamment :

- Microsoft Visual Basic Scripting Edition (VBScript)

- Perl

- Lisp

Pour rendre l’implémentation de l’hôte la plus flexible possible, un wrapper OLE Automation pour Windows Script est fourni. Toutefois, un hôte qui utilise cet objet de wrapper pour instancier le moteur de script n’a pas le même degré de contrôle sur l’espace de noms d’exécution, le modèle de persistance, et ainsi de suite, que celui dont il disposerait s’il utilisait Windows Script directement.

La conception de Windows Script isole les éléments d’interface requis uniquement dans un environnement de création, afin que les moteurs de script (par exemple VBScript) et les hôtes (par exemple les navigateurs et les visionneuses) qui ne sont pas concernés par la création puissent rester le plus légers possible.

## <a name="windows-script-basic-architecture"></a>Architecture de base de Windows Script

L’illustration suivante montre l’interaction entre un hôte Windows Script et un moteur Windows Script.

Les étapes de l’interaction entre l’hôte et le moteur sont présentées dans la liste suivante.

1.  Créez un projet. L’hôte charge un projet ou un document. (Cette étape n’est pas propre à Windows Script, mais elle est incluse ici par souci d’exhaustivité.)

2.  Créer le moteur Windows Script. L’hôte appelle `CoCreateInstance` pour créer un moteur Windows Script, en spécifiant l’identificateur de classe (CLSID) du moteur de script spécifique à utiliser. Par exemple, le navigateur HTML d’Internet Explorer reçoit l’identificateur de classe du moteur de script par le biais de l’attribut CLSID= de la balise HTML \<OBJECT>.

3.  Charger le script. Si le contenu du script a été conservé, l’hôte appelle la méthode `IPersist*::Load` du moteur de script afin de lui transmettre le conteneur des propriétés, le flux ou le stockage de script. Sinon, l’hôte utilise la méthode `IPersist*::InitNew` ou [IActiveScriptParse::InitNew](../winscript/reference/iactivescriptparse-initnew.md) pour créer un script de valeur null. Un hôte qui tient à jour un script sous forme de texte peut utiliser [IActiveScriptParse::ParseScriptText](../winscript/reference/iactivescriptparse-parsescripttext.md) pour transmettre au moteur de script le texte du script, après avoir appelé `IActiveScriptParse::InitNew`.

4.  Ajouter des éléments nommés. Pour chaque élément nommé de niveau supérieur (tels que les pages et les formulaires) importé dans l’espace de noms du moteur de script, l’hôte appelle la méthode [IActiveScript::AddNamedItem](../winscript/reference/iactivescript-addnameditem.md) pour créer une entrée dans l’espace de noms du moteur. Cette étape n’est pas nécessaire si les éléments nommés de niveau supérieur font déjà partie de l’état permanent du script chargé à l’étape 3. Un hôte n’utilise pas `IActiveScript::AddNamedItem` pour ajouter des éléments nommés d’un sous-niveau (tels que les contrôles dans une page HTML). Au lieu de cela, le moteur obtient indirectement les éléments des sous-niveaux à partir des éléments de niveau supérieur en utilisant les interfaces `ITypeInfo` et `IDispatch` de l’hôte.

5.  Exécuter le script. L’hôte fait en sorte que le moteur commence à exécuter le script en définissant l’indicateur SCRIPTSTATE_CONNECTED dans la méthode [IActiveScript::SetScriptState](../winscript/reference/iactivescript-setscriptstate.md). Cet appel effectuerait probablement tout le travail de construction du moteur de script, notamment la liaison statique, le raccordement aux événements (voir ci-dessous) et l’exécution du code, de manière similaire à une fonction `main()` à base de script.

6.  Obtenir les informations sur les éléments. Chaque fois que le moteur de script doit associer un symbole à un élément de niveau supérieur, il appelle la méthode [IActiveScriptSite::GetItemInfo](../winscript/reference/iactivescriptsite-getiteminfo.md), qui retourne des informations sur l’élément en question.

7.  Raccorder les événements. Avant de démarrer le script, le moteur de script se connecte aux événements de tous les objets concernés par le biais de l’interface `IConnectionPoint`.

8.  Appeler les propriétés et méthodes. Lors de l’exécution du script, le moteur de script réalise les références aux méthodes et aux propriétés sur des objets nommés par le biais de `IDispatch::Invoke` ou d’autres mécanismes de liaison OLE standard.

## <a name="windows-script-terms"></a>Termes relatifs à Windows Script

Cette liste contient les définitions des termes relatifs à l’écriture de scripts utilisés dans ce document.

|Terme|Définition|
|----------|----------------|
|Objet de code|Instance créée par le moteur de script et associée à un élément nommé, tel que le module derrière un formulaire dans Visual Basic, ou une classe C++ associée à un élément nommé. Il s’agit de préférence d’un objet OLE COM (Component Object Model) qui prend en charge OLE Automation, afin que l’hôte ou une autre entité non-script puisse manipuler l’objet de code.|
|Élément nommé|Objet OLE COM (de préférence un objet qui prend en charge OLE Automation) que l’hôte juge intéressant pour le script. Il peut s’agir entre autres des objets Page HTML et Navigateur dans un navigateur web, et des objets Document et Boîtes de dialogue dans Microsoft Word.|
|Script|Données qui composent le programme exécuté par le moteur de script. Un script peut être constitué de n’importe quelles données exécutables contiguës, notamment des éléments de texte, des blocs de `pcode`, ou même des codes d’octets exécutables propres à l’ordinateur. Un hôte charge un script dans le moteur de script par le biais de l’une des interfaces `IPersist*` ou de l’interface [IActiveScriptParse](../winscript/reference/iactivescriptparse.md).|
|Moteur de script|Objet OLE qui traite les scripts. Un moteur de script implémente l’interface [IActiveScript](../winscript/reference/iactivescript.md) et, éventuellement, [IActiveScriptParse](../winscript/reference/iactivescriptparse.md).|
|Hôte de script|Application ou programme propriétaire du moteur Windows Script. L’hôte implémente l’interface [IActiveScriptSite](../winscript/reference/iactivescriptsite.md) et, éventuellement, [IActiveScriptSiteWindow](../winscript/reference/iactivescriptsitewindow.md).|
|Scriptlet|Partie d’un script qui est rattachée à un objet par le biais de l’interface [IActiveScriptParse](../winscript/reference/iactivescriptparse.md). La collection agrégée des scriptlets constitue le script.|
|Langage de script|Langage dans lequel un script est écrit (par exemple VBScript), et sémantique de ce langage.|