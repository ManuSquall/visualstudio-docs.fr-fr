---
title: "L’inscription d’un Service2 de langage h&#233;rit&#233; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "inscription, les services de langage"
  - "services de langage, les informations du Registre"
  - "Registre, services de langage"
ms.assetid: ca312aa3-f9f1-4572-8553-89bf3a724deb
caps.latest.revision: 24
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 24
---
# L’inscription d’un Service de langage h&#233;rit&#233;
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Les sections suivantes fournissent des listes d’entrées de Registre pour la langue différentes options de service disponibles dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 Dans la liste suivante des entrées de Registre, *VS Reg racine* est égal à HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\*X.Y*, où *X.Y* est la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] numéro de version.  
  
## Entrées de Registre pour les Options de Service de langage  
 Le *VS Reg racine*\\Languages\\Language Services\\*nom de la langue* clé peut contenir les valeurs suivantes.  
  
|Nom|Type|Plage|Description|  
|---------|----------|-----------|-----------------|  
|\(Default\)|REG\_SZ|*\< GUID \>*|GUID du service de langage.|  
|LangResID|REG\_DWORD|0 x 0\-0xffff|Identificateur de ressource \(ResID\) pour le nom localisé de la langue de la chaîne.|  
|Package|REG\_SZ|*\< GUID \>*|GUID du package VS.|  
|ShowCompletion|REG\_DWORD|0\-1|Spécifie si les **semi\-automatique** options dans le **Options** boîte de dialogue sont activés.|  
|ShowSmartIndent|REG\_DWORD|0\-1|Spécifie si l’option sélectionner **Smart** mise en retrait dans les **Options** boîte de dialogue est activée.|  
|RequestStockColors|REG\_DWORD|0\-1|Spécifie si personnalisés ou les couleurs par défaut sont utilisés pour colorer des mots clés.|  
|ShowHotURLs|REG\_DWORD|0\-1|Spécifie si l’utilisateur peut cliquer sur des URL.|  
|Par défaut, les URL Non réactifs|REG\_DWORD|0\-1|Spécifie le paramètre initial pour le **Activer la navigation dans les URL par simple clic** option dans le **Options** boîte de dialogue.|  
|DefaultToInsertSpaces|REG\_DWORD|0\-1|Spécifie si le service de langage a « Insérer des espaces » en tant que son option de l’onglet par défaut.|  
|ShowDropdownBarOption|REG\_DWORD|0\-1|Active ou désactive le **barre de Navigation** option dans le **Options** boîte de dialogue qui affiche ou masque le **barre de Navigation**.|  
|Que la fenêtre de Code unique|REG\_DWORD|0\-1|Active ou désactive le **nouvelle fenêtre** choix dans le **fenêtre** menu pour un service de langage.|  
|EnableAdvancedMembersOption|REG\_DWORD|0\-1|Active ou désactive un **Options** paramètre de la boîte de dialogue zone **Masquer les membres avancés**.|  
|Prise en charge CF\_HTML|REG\_DWORD|0\-1|Spécifie si l’éditeur permet de copier et coller des données HTML.|  
|EnableLineNumbersOption|REG\_DWORD|0\-1|Spécifie si les **les numéros de ligne** options dans le **Options** boîte de dialogue est activée pour un service de langage.|  
|HideAdvancedMembersByDefault|REG\_DWORD|0\-1|Spécifie si les membres avancés tels que les champs privés sont masquées dans les listes de saisie semi\-automatique.|  
|ShowBraceCompletion|REG\_DWORD|0\-1|Spécifie si les **fin d’accolade** option dans le **Options** boîte de dialogue est activée.|  
  
### Exemple  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\  
  Languages\  
    Language Services\  
      C/C++\  
        (Default)             = reg_sz:{B2F072B0-ABC1-11D0-9D62-00C04FD9DFD9}  
        LangResID             = reg_dword:0x00000000  
        Package               = reg_sz:{8C2EA640-ABC1-11D0-9D62-00C04FD9DFD9}  
        ShowCompletion        = reg_dword:0x00000001  
        ShowSmartIndent       = reg_dword:0x00000001  
        ShowDropdownBarOption = reg_dword:0x00000001  
```  
  
## Entrées de Registre pour les Options du débogueur langues  
 Le *VS Reg racine*\\Languages\\Language Services\\*nom de la langue*\\Debugger Languages\\*GUID*\\ clé peut inclure les valeurs suivantes.  
  
|Nom|Type|Plage|Description|  
|---------|----------|-----------|-----------------|  
|\(Default\)|REG\_SZ|texte|La valeur par défaut peut être utilisée pour documenter le nom de la langue. Le nom de cette clé est un GUID d’un évaluateur d’expression qui a une entrée correspondante dans *\< VS Reg racine \>*\\AD7Metrics\\Expression évaluateur.|  
  
### Exemple  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\  
  Languages\  
    Language Services\  
      C/C++\  
        Debugger Languages\  
          {3A12D0B7-C26C-11D0-B442-00A0244A1DD2}\  
            (Default) = reg_sz:C++  
```  
  
## Entrées de Registre pour les Options d’outils de l’éditeur  
 Vous pouvez ajouter des clés de Registre sous la clé EditorToolsOptions pour les pages de propriétés et les nœuds de la propriété. Ces clés et leurs valeurs identifient les pages de propriétés de la **Options** boîte de dialogue \(sur le **outils** menu\) qui sont utilisés pour configurer le service de langage. Dans l’exemple suivant, *nom de la Page* est le nom d’une page de propriétés, et *nom de nœud* est le nom d’un nœud dans l’arborescence sur le **Options** boîte de dialogue. L’entrée de la page et l’entrée du nœud doivent être spécifiées séparément.  
  
|Nom|Type|Plage|Description|  
|---------|----------|-----------|-----------------|  
|\(Default\)|REG\_SZ|ResID|Le nom complet localisé de cette page d’options. Le nom peut être texte littéral ou \#`nnn`, où `nnn` est un ID de ressource de chaîne dans la DLL du package VS spécifié satellite.|  
|Package|REG\_SZ|*GUID*|GUID du package VS qui implémente cette page d’options.|  
|Page|REG\_SZ|*GUID*|Le GUID de la page de propriétés pour demander le VSPackage en appelant le <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> \(méthode\). Si cette entrée de Registre n’est pas présente, la clé de Registre décrit un nœud, pas une page.|  
  
### Exemple  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\  
  Languages\  
    Language Services\  
      CSharp\  
        EditorToolsOptions\  
          Formatting\  
            (Default) = reg_sz:#242  
            Package   = reg_sz:{A066E284-DCAB-11D2-B551-00C04F68D4DB}  
            General\  
              (Default) = reg_sz:#255  
              Package   = reg_sz:{A066E284-DCAB-11D2-B551-00C04F68D4DB}  
              Page      = reg_sz:{3EB2CC0B-033E-4D75-B26A-B2362C25227E}  
            Indentation\  
              (Default) = reg_sz:#250  
              Package   = reg_sz:{A066E284-DCAB-11D2-B551-00C04F68D4DB}  
              Page      = reg_sz:{5E21D017-6D2A-4114-A1F1-C923F001CBBB}  
            Newlines\  
              (Default) = reg_sz:#253  
              Package   = reg_sz:{A066E284-DCAB-11D2-B551-00C04F68D4DB}  
              Page      = reg_sz:{607D8062-68D1-41E4-9A35-B5E7F14D0481}  
```  
  
## Entrées de Registre pour les Options d’Extension de nom de fichier  
 L’entrée pour l’extension de fichier doit inclure le point de début, par exemple « .myext ».  
  
|Nom|Type|Plage|Description|  
|---------|----------|-----------|-----------------|  
|\(Default\)|REG\_SZ|*GUID*|GUID du service pour le service de langage par défaut pour ce type d’extension de nom du fichier.|  
  
### Exemple  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\  
  Languages\  
    File Extensions\  
      .cpp\  
        (Default) = {B2F072B0-ABC1-11D0-9D62-00C04FD9DFD9}  
```  
  
## Entrées de Registre pour les Options de l’éditeur  
 Le *VS Reg racine*\\Editors clé peut contenir les valeurs suivantes :  
  
|Nom|Type|Plage|Description|  
|---------|----------|-----------|-----------------|  
|\(Default\)|REG\_SZ|""|N’est pas utilisé ; Vous pouvez placer votre nom ici pour la documentation.|  
|DefaultToolboxTab|REG\_SZ|""|Nom de l’onglet Boîte à outils à utiliser par défaut lorsque l’éditeur est actif.|  
|DisplayName|REG\_SZ|ResID|Nom à afficher dans le **Ouvrir avec** boîte de dialogue. Le nom est l’ID de ressource de chaîne ou un nom de format standard.|  
|ExcludeDefTextEditor|REG\_DWORD|0\-1|Utilisé pour le **Ouvrir avec** commande de menu. Si vous ne souhaitez pas que l’éditeur de texte par défaut dans la liste des éditeurs disponibles pour un type de fichier de la liste, définissez cette valeur sur 1.|  
|LinkedEditorGUID|REG\_SZ|*\< GUID \>*|Utilisé pour n’importe quel service de langage qui peut ouvrir un fichier avec prise en charge de la page de codes. Par exemple, lorsque vous ouvrez un fichier .txt à l’aide de la **Ouvrir avec** commande, les options sont fournies pour l’utilisation de l’éditeur de code source avec et sans encodage.<br /><br /> Le GUID spécifié dans le nom de la sous\-clé est pour la fabrique d’éditeur de page de codes ; le GUID lié spécifié dans cette entrée de Registre spécifique est pour la fabrique d’éditeur régulière. L’objectif de cette entrée est que, si l’IDE ne s’ouvre pas un fichier à l’aide de l’éditeur par défaut, l’IDE tente d’utiliser l’éditeur suivant dans la liste. Cet éditeur suivant ne doit pas être la fabrique d’éditeur de page de codes, car cette fabrique d’éditeur est essentiellement le même que la fabrique d’éditeur qui a échoué.|  
|Package|REG\_SZ|*\< GUID \>*|VSPackage GUID pour ResID du nom affichage.|  
  
### Exemple  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\  
  \Editors\  
    {8281C572-2171-45AA-A642-7D8BC1662F1C}\  
      (Default)            = reg_sz:Html Editor with Encoding  
      DefaultToolboxTab    = reg_sz:HTML  
      DisplayName          = reg_sz:#20101  
      LinkedEditorGUID     = reg_sz:{C76D83F8-A489-11D0-8195-00A0C91BBEE3}  
      Package              = reg_sz:{1B437D20-F8FE-11D2-A6AE-00104BCC7269}  
```  
  
## Entrées de Registre pour les Options de vue logique  
 Le *VS Reg racine*\\Editors\\*éditeur graphique \>*\\LogicalViews clé peut contenir les valeurs suivantes.  
  
|Nom|Type|Plage|Description|  
|---------|----------|-----------|-----------------|  
|\(Default\)|REG\_SZ||Inutilisé.|  
|*\< GUID \>*|REG\_SZ|""|Clé pour les vues logiques pris en charge. Vous pouvez avoir autant que nécessaire. Le nom de l’entrée de Registre est ce qui est important, pas la valeur, qui est toujours une chaîne vide.|  
  
### Exemple  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\  
  \Editors\  
    {8281C572-2171-45AA-A642-7D8BC1662F1C}\  
      LogicalViews\  
       (Default) = reg_sz:  
       {7651a700-06e5-11d1-8ebd-00a0c90f26ea} = reg_sz:  
       {7651a701-06e5-11d1-8ebd-00a0c90f26ea} = reg_sz:  
       {7651a702-06e5-11d1-8ebd-00a0c90f26ea} = reg_sz:  
       {7651a703-06e5-11d1-8ebd-00a0c90f26ea} = reg_sz:  
```  
  
## Entrées de Registre pour les Options d’Extension de l’éditeur  
 Le *VS Reg racine*\\Editors\\*éditeur GUID*\\Extensions clé peut contenir les valeurs suivantes. L’extension de nom de fichier n’inclut pas le point de début.  
  
|Nom|Type|Plage|Description|  
|---------|----------|-----------|-----------------|  
|\(Default\)|REG\_SZ||Inutilisé.|  
|*\< ext \>*|REG\_DWORD|0\-0xffffffff.|Priorité relative des extensions. Si deux ou plusieurs langues partagent la même extension, la langue de priorité plus élevée est choisie.|  
  
 En outre, sélection par défaut de l’utilisateur actuel pour un éditeur est stockée dans HKEY\_Current\_User\\Software\\Microsoft\\VisualStudio\\*X.Y*\\Default Editors\\*ext*. Le GUID du service de langage sélectionné est dans l’écriture personnalisée. Cela est prioritaire pour l’utilisateur actuel.  
  
### Exemple  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0\  
  \Editors\  
    {8281C572-2171-45AA-A642-7D8BC1662F1C}\  
      Extensions\  
       (Default) = reg_sz:  
       *         = reg_dword:0x00000018  
       html      = reg_dword:0x00000027  
       shtm      = reg_dword:0x00000027  
       shtml     = reg_dword:0x00000027  
```  
  
## Entrées du Registre des Options de Service de langage Framework Package managé  
 Les entrées de Registre suivantes sont spécifiques pour les classes de service de langage managé package framework \(MPF\). Ces entrées de Registre indiquent la prise en charge dans le service de langage pour diverses fonctionnalités IntelliSense et d’autres fonctionnalités d’éditions avancées.  
  
 Ces entrées de Registre sont accessibles via la <xref:Microsoft.VisualStudio.Package.LanguagePreferences> classe.  
  
|Nom|Type|Plage|Description|  
|---------|----------|-----------|-----------------|  
|CodeSense|REG\_DWORD|0\-1|Prise en charge pour les opérations d’IntelliSense.|  
|MatchBraces|REG\_DWORD|0\-1|Prise en charge pour la correspondance des paires de langage telles que des accolades, parenthèses et crochets.|  
|Info express|REG\_DWORD|0\-1|Prise en charge pour l’opération Info express IntelliSense.|  
|ShowMatchingBrace|REG\_DWORD|0\-1|Prise en charge pour l’affichage de la paire de langue correspondante dans la barre d’état.|  
|MatchBracesAtCaret|REG\_DWORD|0\-1|Prise en charge pour l’affichage des paires correspondantes de langage, généralement via les deux éléments de mise en surbrillance.|  
|MaxErrorMessages|REG\_DWORD|0\-n|Le nombre maximal d’erreurs qui peuvent être affichés dans le **liste d’erreurs** fenêtre.|  
|CodeSenseDelay|REG\_DWORD|0\-n|Le nombre de millisecondes à attendre avant de lancer n’importe quel arrière\-plan l’analyse pour une opération d’IntelliSense.|  
|EnableAsyncCompletion|REG\_DWORD|0\-1|Prise en charge pour l’analyse en arrière\-plan.|  
|EnableCommenting|REG\_DWORD|0\-1|Prise en charge pour commenter les blocs de texte sélectionnés et implique également la prise en charge pour le texte sélectionné de supprimer le commentaire.|  
|EnableFormatSelection|REG\_DWORD|0\-1|Prise en charge pour la mise en forme de texte tel qu’auto\-mise en retrait ou d’ajustement de la position des accolades.|  
|AutoOutlining|REG\_DWORD|0\-1|Prise en charge \(régions qui peuvent être réduites\) en mode plan.|  
|MaxRegions|REG\_DWORD|0\-n|Le nombre maximal de zones masquées par fichier.|  
  
```  
ExampleHKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\  
  Languages\  
    Language Services\  
      XML\  
        (Default)             = reg_sz:{f6819a78-a205-47b5-be1c-675b3c7f0b8e}  
        MatchBraces           = reg_dword:0x00000001  
        QuickInfo             = reg_dword:0x00000001  
        ShowMatchingBrace     = reg_dword:0x00000001  
        MatchBracesAtCaret    = reg_dword:0x00000000  
        MaxErrorMessages      = reg_dword:0x00000064  
        CodeSenseDelay        = reg_dword:0x000001f4  
        MaxRegions            = reg_dword:0x0000000a  
```  
  
## Voir aussi  
 [Développement d'un Service de langage](../../extensibility/internals/developing-a-legacy-language-service.md)