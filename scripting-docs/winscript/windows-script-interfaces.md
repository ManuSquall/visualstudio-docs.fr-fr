---
title: "Windows Script, interfaces | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4c750627-6797-4857-9f5e-e5f54371f83c
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# Windows Script, interfaces
Les interfaces de script Microsoft Windows permettent d'application d'ajouter script et OLE automation.  Les hôtes de Script qui dépendent Windows Script peuvent utiliser des moteurs de script plusieurs sources et de constructeurs pour gérer script entre les composants.  L'implémentation du soi\-même\- langage de script, syntaxe, format persistant, modèle d'exécution, etc. dessus est laissée au constructeur de script.  
  
 La documentation de Windows Script est divisé en sections suivantes :  
  
 [Windows Script Hosts](../winscript/windows-script-hosts.md)  
  
 [Windows Script, moteurs](../winscript/windows-script-engines.md)  
  
 [Débogage de script actif, présentation](../winscript/active-script-debugging-overview.md)  
  
 [Profilage de script actif, présentation](../winscript/active-script-profiling-overview.md)  
  
 [Interfaces Windows Script, référence](../winscript/reference/windows-script-interfaces-reference.md)  
  
## Arrière\-plan de Windows Script  
 Les interfaces de Windows Script sont répartis en deux catégories : Hôtes Windows Script et moteurs de Script Windows.  Un hôte crée un moteur de script et de faire appel au moteur pour exécuter les scripts.  Les hôtes Windows Script incluent :  
  
-   Microsoft Internet Explorer  
  
-   Outils de création Internet  
  
-   Shell  
  
 Les moteurs de Windows Script peuvent être développées pour tout langage ou environnement d'exécution, notamment :  
  
-   Microsoft Visual Basic Scripting Edition \(VBScript\)  
  
-   Perl  
  
-   Lisp  
  
 Pour rendre l'implémentation de l'hôte et flexible possible, un wrapper OLE Automation pour Windows Script est fourni.  Toutefois, un hôte qui utilise cet objet de wrapper pour instancier le moteur de script n'a pas le degré de contrôle de l'espace de noms à l'exécution, le modèle de persistance, etc., qu'il s'il utilisait Windows Script directement.  
  
 La conception de Windows Script isole les éléments d'interface requis uniquement dans un environnement de création de sorte que les hôtes nonauthoring \(tels que des navigateurs et des visionneuses\) et des moteurs de script \(par exemple, VBScript\) peuvent être conservés légers.  
  
## Architecture de base Windows Script  
 L'illustration suivante montre l'interaction entre un hôte Windows Script et un moteur de Script Windows.  
  
 Les étapes dans l'interaction entre l'hôte et le moteur sont données dans la liste suivante.  
  
1.  Créez un projet.  L'hôte charge un projet ou un document.  \(Cette étape n'est pas spécifique à Windows Script, mais est incluse ici à des fins de précision.\)  
  
2.  Créez le moteur de Script Windows.  L'hôte appelle `CoCreateInstance` pour créer une nouvelle moteur de Script Windows, en spécifiant l'identificateur de classe \(CLSID\) du moteur de script spécifique à utiliser.  Par exemple, le navigateur HTML Internet Explorer reçoit l'identificateur de classe du moteur de script via l'attribut de CLSID\= de la balise d' \<OBJECT\> HTML.  
  
3.  Chargez le script.  Si le contenu de script a été rendu persistant, l'hôte appelle la méthode d' `IPersist*::Load` du moteur de script pour distribuer en mémoire, le flux, ou le conteneur des propriétés de script.  Sinon, l'hôte utilise `IPersist*::InitNew` ou la méthode d' [IActiveScriptParse::InitNew](../winscript/reference/iactivescriptparse-initnew.md) pour créer un script null.  Un hôte qui met à jour un script comme texte peut utiliser [IActiveScriptParse::ParseScriptText](../winscript/reference/iactivescriptparse-parsescripttext.md) pour distribuer au moteur de script le texte du script, après avoir appelé `IActiveScriptParse::InitNew`.  
  
4.  Add nommé des éléments.  Pour chaque niveau supérieur nommé élément \(telles que des pages et des formes\) importé dans l'espace de noms du moteur de script, l'hôte appelle la méthode d' [IActiveScript::AddNamedItem](../winscript/reference/iactivescript-addnameditem.md) pour créer une entrée dans l'espace de noms du moteur.  Cette étape n'est pas nécessaire si les éléments nommés niveau supérieur sont déjà partie de l'état de persistance du script chargé dans l'étape 3.  Un hôte n'utilise pas `IActiveScript::AddNamedItem` pour ajouter des éléments nommés sous\-niveau \(tels que les contrôles sur une page HTML\) ; au contraire, le moteur d'obtenir indirectement des éléments de sous\-niveau les éléments de niveau supérieur en utilisant des interfaces d' `ITypeInfo` et d' `IDispatch` de l'hôte.  
  
5.  Exécutez le script.  L'hôte fait démarrer le moteur exécuter le script en définissant l'indicateur de SCRIPTSTATE\_CONNECTED dans la méthode d' [IActiveScript::SetScriptState](../winscript/reference/iactivescript-setscriptstate.md) .  Cet appel effectuerait probablement un travail de construction du moteur de script, y compris la liaison statique, s'accrochant jusqu'à des événements \(voir ci\-dessous\), et l'exécution du code, d'une manière similaire à une fonction préétablie d' `main()` .  
  
6.  Obtenez des informations d'élément.  Chaque fois que le moteur de script doit associer un symbole avec un élément de niveau supérieur, il appelle la méthode d' [IActiveScriptSite::GetItemInfo](../winscript/reference/iactivescriptsite-getiteminfo.md), qui retourne des informations sur l'élément donné.  
  
7.  Raccorder les événements.  Avant de démarrer le script réel, le moteur de script se connecte aux événements de tous les objets appropriés via l'interface d' `IConnectionPoint` .  
  
8.  Appelez les propriétés et les méthodes.  Lorsque le script s'exécute, le moteur de script réalise des références aux méthodes et des propriétés sur les objets nommés via `IDispatch::Invoke` ou d'autres OLE mécanismes de liaison standard.  
  
## Termes de Windows Script  
 Cette liste contient les définitions des termes liés au script utilisés dans ce document.  
  
|Terme|Définition|  
|-----------|----------------|  
|Objet de code|Une instance créée par le moteur de script qui est associé à un élément nommé, tel que le module derrière un formulaire en Visual Basic, ou la classe c\+\+ associée à un élément nommé.  De préférence, il s'agit d'un objet de \(COM\) du modèle objet composant OLE qui prend en charge OLE Automation l'hôte ou toute autre entité non script peut manipuler l'objet de code.|  
|Élément nommé|OLE un objet COM \(de préférence un qui prend en charge OLE Automation\) qui l'hôte prend en considération intéressant au script.  Les exemples incluent la page HTML et le navigateur dans un navigateur web, et le document et les boîtes dans Microsoft Word.|  
|Script|Les données qui composent le programme que le moteur de script active.  Un script peut être toutes les données contiguës exécutables, notamment les parties de texte, de blocs d' `pcode`, voire de codes exécutables propres à un ordinateur d'octets.  Un hôte charge un script dans le moteur de script via une des interfaces d' `IPersist*` ou via l'interface d' [IActiveScriptParse](../winscript/reference/iactivescriptparse.md) .|  
|Moteur de script|L'objet OLE qui traite les scripts.  Un moteur de script implémente les interfaces d' [IActiveScript](../winscript/reference/iactivescript.md) et, éventuellement, d' [IActiveScriptParse](../winscript/reference/iactivescriptparse.md) .|  
|Hôte de Script|L'application ou le programme qui possèdent le moteur de Script Windows.  L'hôte implémente les interfaces d' [IActiveScriptSite](../winscript/reference/iactivescriptsite.md) et, éventuellement, d' [IActiveScriptSiteWindow](../winscript/reference/iactivescriptsitewindow.md) .|  
|Scriptlet|Une partie d'un script qui obtient s'est attachée à un objet via l'interface d' [IActiveScriptParse](../winscript/reference/iactivescriptparse.md) .  La collection globale de scriptlets est le script.|  
|Langage de script|Le langage dans lequel un script est écrit \(VBScript, par exemple\) et la sémantique de ce langage.|  
  
## Voir aussi  
 [Windows Script Interfaces](../winscript/windows-script-interfaces.md)