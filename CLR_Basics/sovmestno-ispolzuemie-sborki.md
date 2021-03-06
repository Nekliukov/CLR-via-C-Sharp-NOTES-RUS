# Совместно используемые сборки

До этого говорилось о построении, упаковке и развертывании сборок. При этом основное внимание уделялось **закрытому развертыванию \(private deployment\)**, при котором сборки, предназначенные исключительно для одного приложения, помещают в базовый каталог приложения или в его подкаталог. Закрытое развертывание сборок позволяет в значительной мере управлять именами, версиями и поведением сборок. 

Сборки, которые могут исполшьзоваться несколькими приложениями называются** глобальными. **Замечательный пример глобально развертываемых сборок — это сборки, поставляемые вместе с Microsoft .NET Framework, поскольку почти все управляемые приложения используют типы, определенные Microsoft в библиотеке классов .NET Framework Class Library \(FCL\). 

CLR поддерживает два вида сборок:

1. Со строгими именами
2. С нестрогими именами

### Назначение сборке строгого имени

Если сборка должна использоваться несколькими приложениями, ее следует поместить в общеизвестный каталог, который среда CLR должна автоматически проверять, обнаружив ссылку на сборку. Однако при этом возникает проблема — две \(или больше\) компании могут выпустить сборки с одинаковыми именами. Тогда, если обе эти сборки будут скопированы в один общеизвестный каталог, «победит» последняя из них, а работа приложений, использовавших первую, нарушится — ведь первая при копировании заменяется второй \(это и является причиной «кошмара DLL» в современных системах Windows — все библиотеки DLL копируются в папку System32\).

Очевидно, одного имени файла мало, чтобы различать две сборки. Среда CLR должна поддерживать некий механизм, позволяющий уникально идентифицировать сборку. Именно для этого и служат строгие имена. У сборки со строгим именем четыре атрибута, уникально ее идентифицирующих: имя файла \(без расширения\), номер версии, идентификатор регионального стандарта и открытый ключ. Поскольку открытые ключи представляют собой очень большие числа, вместо последнего атрибута используется небольшой хеш-код открытого ключа, который называют маркером открытого ключа \(public key token\). Следующие четыре строки, которые иногда называют отображаемым именем сборки \(assembly display name\), идентифицируют совершенно разные файлы сборки: 

"MyTypes, Version=1.0.8123.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"  "MyTypes, Version=1.0.8123.0, Culture="en-US", PublicKeyToken=b77a5c561934e089"  "MyTypes, Version=2.0.1234.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" "MyTypes, Version=1.0.8123.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a" 

