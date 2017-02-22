---
title: "DisassemblyData | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DisassemblyData"
helpviewer_keywords: 
  - "Structure de DisassemblyData"
ms.assetid: 10e70aa7-9381-40d3-bdd1-d2cad78ef16c
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# DisassemblyData
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Décrit une instruction de code machine pour l'environnement de \(IDE\) développement intégré à afficher.  
  
## Syntaxe  
  
```cpp#  
typedef struct tagDisassemblyData {   
   DISASSEMBLY_STREAM_FIELDS dwFields;  
   BSTR                      bstrAddress;  
   BSTR                      bstrAddressOffset;  
   BSTR                      bstrCodeBytes;  
   BSTR                      bstrOpcode;  
   BSTR                      bstrOperands;  
   BSTR                      bstrSymbol;  
   UINT64                    uCodeLocationId;  
   TEXT_POSITION             posBeg;  
   TEXT_POSITION             posEnd;  
   BSTR                      bstrDocumentUrl;  
   DWORD                     dwByteOffset;  
   DISASSEMBLY_FLAGS         dwFlags;  
} DisassemblyData;  
```  
  
```c#  
public struct DisassemblyData {   
   public uint          dwFields;  
   public string        bstrAddress;  
   public string        bstrAddressOffset;  
   public string        bstrCodeBytes;  
   public string        bstrOpcode;  
   public string        bstrOperands;  
   public string        bstrSymbol;  
   public ulong         uCodeLocationId;  
   public TEXT_POSITION posBeg;  
   public TEXT_POSITION posEnd;  
   public string        bstrDocumentUrl;  
   public uint          dwByteOffset;  
   public uint          dwFlags;  
};  
```  
  
## Membres  
 `dwFields`  
 La constante de [DISASSEMBLY\_STREAM\_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md) qui spécifie quels champs sont remplis.  
  
 `bstrAddress`  
 L'adresse comme un offset d'un certain point de départ \(généralement le début de la fonction associée\).  
  
 `bstrCodeBytes`  
 les octets de code pour cette instruction.  
  
 `bstrOpcode`  
 L'opcode pour cette instruction.  
  
 `bstrOperands`  
 les opérandes pour cette instruction.  
  
 `bstrSymbol`  
 Le nom du symbole, le cas échéant, associé à l'adresse \(symbole, nom publics, etc.\).  
  
 `uCodeLocationId`  
 L'identificateur de l'emplacement du code pour cette ligne désassemblée.  Si l'adresse de contexte de code d'une ligne est supérieure à l'adresse de contexte de code des autres, l'identificateur désassemblé d'emplacement du code du premier sera également plus grand que l'identificateur de l'emplacement du code de la seconde.  
  
 `posBeg`  
 [TEXT\_POSITION](../../../extensibility/debugger/reference/text-position.md) qui correspond à la position dans un document où les données de code machine démarre.  
  
 `posEnd`  
 [TEXT\_POSITION](../../../extensibility/debugger/reference/text-position.md) qui correspond à la position dans un document où les données de code machine se termine.  
  
 `bstrDocumentUrl`  
 Pour les documents texte qui peuvent être représentés en tant que noms de fichiers, le champ d' `bstrDocumentUrl` est rempli avec le nom de fichier où la source est trouvée, au format `nom de file://file`.  
  
 Pour les documents texte qui ne peuvent pas être représentés en tant que noms de fichiers, `bstrDocumentUrl` est un identificateur unique pour le document, et le moteur de débogage doit implémenter la méthode d' [GetDocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md) .  
  
 Ce champ peut également contenir des informations supplémentaires sur les checksums.  Voir notes pour plus de détails.  
  
 `dwByteOffset`  
 Le nombre d'octets l'instruction est du début de la ligne de code.  
  
 `dwFlags`  
 La constante de [DISASSEMBLY\_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md) qui spécifie les balises actives.  
  
## Notes  
 chaque structure d' `DisassemblyData` décrit une instruction de code machine.  Un tableau de ces structures est retourné par la méthode d' [Lecture](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) .  
  
 La structure de [TEXT\_POSITION](../../../extensibility/debugger/reference/text-position.md) est utilisée pour les documents basés sur du texte.  La plage de code source pour cette instruction est effectuée uniquement pour la première instruction générée d'une instruction ou d'une ligne, par exemple, lorsque `dwByteOffset == 0`.  
  
 Pour les documents qui sont non\-textuels, un contexte de document peut être obtenu à partir de code, et le champ d' `bstrDocumentUrl` doit être une valeur NULL.  Si le champ d' `bstrDocumentUrl` est identique au champ d' `bstrDocumentUrl` dans l'élément de tableau précédent d' `DisassemblyData` , affectez comme `bstrDocumentUrl` à une valeur NULL.  
  
 Si le champ d' `dwFlags` a la balise d' `DF_DOCUMENT_CHECKSUM` définie, des données supplémentaires de checksum suivent la chaîne désignée par le champ d' `bstrDocumentUrl` .  Spécifiquement, après le terminateur de chaîne Null, il suit un GUID identifiant l'algorithme de checksum qui est ensuite suivi d'une valeur de 4 octets indiquant le nombre d'octets dans le checksum et qui à son tour est suivi par les octets de checksum.  Consultez l'exemple de cette rubrique sur la façon d'encoder et de décoder ce champ dans [!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)].  
  
## Exemple  
 Le champ d' `bstrDocumentUrl` peut contenir des informations supplémentaires autre qu'une chaîne si la balise d' `DF_DOCUMENT_CHECKSUM` est définie.  Le processus de création et de lire cette chaîne encodée est simple dans [!INCLUDE[vcprvc](../../../debugger/includes/vcprvc_md.md)].  Toutefois, dans [!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)], il s'agit d'une autre procédure.  Pour ceux qui sont curieux, l'exemple suivant illustre une manière de créer la chaîne encodée de [!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)] et une méthode pour décoder la chaîne encodée dans [!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)].  
  
```c#  
using System;  
using System.Runtime.InteropServices;  
  
namespace MyNamespace  
    class MyClass  
    {  
        string EncodeData(string documentString,  
                          Guid checksumGuid,  
                          byte[] checksumData)  
        {  
            string returnString = documentString;  
  
            if (checksumGuid == null || checksumData == null)  
            {  
                // Nothing more to do. Just return the string.  
                return returnString;  
            }  
  
            returnString += '\0'; // separating null value  
  
            // Add checksum GUID to string.  
            byte[] guidDataArray  = checksumGuid.ToByteArray();  
            int    guidDataLength = guidDataArray.Length;  
            IntPtr pBuffer        = Marshal.AllocCoTaskMem(guidDataLength);  
            for (int i = 0; i < guidDataLength; i++)  
            {  
                Marshal.WriteByte(pBuffer, i, guidDataArray[i]);  
            }  
            // Copy guid data bytes to string as wide characters.  
            // Assumption: sizeof(char) == 2.  
            for (int i = 0; i < guidDataLength; i++)  
            {  
                returnString += (char)Marshal.ReadInt16(pBuffer, i * sizeof(char));  
            }  
  
            // Add checksum count (a 32-bit value).  
            Int32 checksumCount = checksumData.Length;  
            Marshal.StructureToPtr(checksumCount, pBuffer, true);  
            for (int i = 0; i < sizeof(Int32) / sizeof(char); i++)  
            {  
                returnString += (char)Marshal.ReadInt16(pBuffer, i * sizeof(char));  
            }  
  
            // Add checksum data.  
            pBuffer = Marshal.AllocCoTaskMem(checksumCount);  
            for (int i = 0; i < checksumCount; i++)  
            {  
                Marshal.WriteByte(pBuffer, i, checksumData[i]);  
            }  
            for (int i = 0; i < checksumCount / sizeof(char); i++)  
            {  
                returnString += (char)Marshal.ReadInt16(pBuffer, i * sizeof(char));  
            }  
            Marshal.FreeCoTaskMem(pBuffer);  
  
            return returnString;  
        }  
  
        void DecodeData(    string encodedString,  
                        out string documentString,  
                        out Guid   checksumGuid,  
                        out byte[] checksumData)  
       {  
           documentString = String.Empty;  
           checksumGuid = Guid.Empty;  
           checksumData = null;  
  
           IntPtr pBuffer = Marshal.StringToBSTR(encodedString);  
           if (null != pBuffer)  
           {  
               int bufferOffset = 0;  
  
               // Parse string out.  String is assumed to be Unicode.  
               documentString = Marshal.PtrToStringUni(pBuffer);  
               bufferOffset += (documentString.Length + 1) * sizeof(char);  
  
               // Parse Guid out.  
               // Read guid bytes from buffer and store in temporary  
               // buffer that contains only the guid bytes. Then the  
               // Marshal.PtrToStructure() can work properly.  
               byte[] guidDataArray  = checksumGuid.ToByteArray();  
               int    guidDataLength = guidDataArray.Length;  
               IntPtr pGuidBuffer    = Marshal.AllocCoTaskMem(guidDataLength);  
               for (int i = 0; i < guidDataLength; i++)  
               {  
                   Marshal.WriteByte(pGuidBuffer, i,  
                                     Marshal.ReadByte(pBuffer, bufferOffset + i);  
               }  
               bufferOffset += guidDataLength;  
               checksumGuid = (Guid)Marshal.PtrToStructure(pGuidBuffer, typeof(Guid));  
               Marshal.FreeCoTaskMem(pGuidBuffer);  
  
              // Parse out the number of checksum data bytes (always 32-bit value).  
              int dataCount = Marshal.ReadInt32(pBuffer, bufferOffset);  
              bufferOffset += sizeof(Int32);  
  
              // Parse out the checksum data.  
              checksumData = new byte[dataCount];  
              for (int i = 0; i < dataCount; i++)  
              {  
                  checksumData[i] = Marshal.ReadByte(pBuffer, bufferOffset + i);  
              }  
           }  
       }  
    }  
}  
```  
  
## Voir aussi  
 [Structures et Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [Lecture](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)   
 [DISASSEMBLY\_STREAM\_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [TEXT\_POSITION](../../../extensibility/debugger/reference/text-position.md)   
 [DISASSEMBLY\_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)