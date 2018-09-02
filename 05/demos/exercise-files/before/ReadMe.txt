To follow along with the demo shown in the clips "Inconsistent Test Behavior" and "Maintaining Consistency Across Tests", you'll need to add the following functions to your DataManager object and DataManagerTest class.

Add this function to the DataManager object:
fun findNote(course: CourseInfo, noteTitle: String, noteText: String) : NoteInfo? {
    for(note in notes)
        if (course == note.course &&
                noteTitle == note.title &&
                noteText == note.text)
            return note
    return null
}

Add this function to the DataManagerTest class that you created as part of the demo shown in the clip "Adding a Unit Test":
@Test
fun findSimilarNotes() {
    val course = DataManager.courses.get("android_async")!!
    val noteTitle = "This is a test note"
    val noteText1 = "This is the body of my test note"
    val noteText2 = "This is the body of my second test note"
    val index1 = DataManager.addNote(course, noteTitle, noteText1
    val index2 = DataManager.addNote(course, noteTitle, noteText2
    val note1 = DataManager.findNote(course, noteTitle, noteText1
    val foundIndex1 = DataManager.notes.indexOf(note1)
    assertEquals(index1, foundIndex1)
    val note2 = DataManager.findNote(course, noteTitle, noteText2
    val foundIndex2 = DataManager.notes.indexOf(note2)
    assertEquals(index2, foundIndex2)
}