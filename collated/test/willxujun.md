# willxujun
###### \java\seedu\address\logic\commands\FindCommandTest.java
``` java
    @Test
    /**
     * Changed to noPersonaFound because of new AND search mechanism.
     */
    public void execute_multipleKeywords_noPersonFound() {
        String expectedMessage = String.format(MESSAGE_PERSONS_LISTED_OVERVIEW, 0);
        FindCommand command = prepareCommand("Kurz Elle Kunz");
        assertCommandSuccess(command, expectedMessage, Collections.emptyList());
    }
```
###### \java\seedu\address\logic\parser\AddCommandParserTest.java
``` java
        //empty (unknown) email value
        expectedPerson = new PersonBuilder().withName(VALID_NAME_AMY).withPhone(VALID_PHONE_AMY)
                .withEmail(UNKNOWN_EMAIL).withAddress(VALID_ADDRESS_AMY).withTags().build();
        assertParseSuccess(parser, AddCommand.COMMAND_WORD + NAME_DESC_AMY + PHONE_DESC_AMY
                + UNKNOWN_EMAIL_DESC + ADDRESS_DESC_AMY, new AddCommand(expectedPerson));

        //empty (unknown) address value
        expectedPerson = new PersonBuilder().withName(VALID_NAME_AMY).withPhone(VALID_PHONE_AMY)
                .withEmail(VALID_EMAIL_AMY).withAddress(UNKNOWN_ADDRESS).withTags().build();
        assertParseSuccess(parser, AddCommand.COMMAND_WORD + NAME_DESC_AMY + PHONE_DESC_AMY
                + EMAIL_DESC_AMY + UNKNOWN_ADDRESS_DESC, new AddCommand(expectedPerson));
```
###### \java\systemtests\AddCommandSystemTest.java
``` java
        /* Case: unknown address -> added*/
        toAdd = new PersonBuilder().withName(VALID_NAME_AMY).withPhone(VALID_PHONE_AMY)
                .withEmail(VALID_EMAIL_AMY).withAddress(UNKNOWN_ADDRESS).withTags().build();
        command = AddCommand.COMMAND_WORD + NAME_DESC_AMY + PHONE_DESC_AMY + EMAIL_DESC_AMY + UNKNOWN_ADDRESS_DESC;
        assertCommandSuccess(command, toAdd);
```
###### \java\systemtests\EditCommandSystemTest.java
``` java
        /* Case: edit a person with new values same as existing values -> edited */
        /* Disabled test case: because each edit reshuffles the person list, this test case will fail as a result of
        sorting mechanism.
        command = EditCommand.COMMAND_WORD + " " + index.getOneBased() + NAME_DESC_BOB + PHONE_DESC_BOB + EMAIL_DESC_BOB
                + ADDRESS_DESC_BOB + TAG_DESC_FRIEND + TAG_DESC_HUSBAND;
        assertCommandSuccess(command, index, BOB);
        */
```
###### \java\systemtests\FindCommandSystemTest.java
``` java
        /* Case: find multiple persons in address book, 2 keywords -> 0 persons found because of new AND search*/
        command = FindCommand.COMMAND_WORD + " Benson Daniel";
        ModelHelper.setFilteredList(expectedModel);
        assertCommandSuccess(command, expectedModel);
        assertSelectedCardUnchanged();
```
