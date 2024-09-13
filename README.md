To replicate this exact Prod issue locally:

// AppCompatActivityAwareHelper.kt
override fun addOnActivityAvailableListener(listener: OnActivityAvailableListener) {
  listeners.add(listener)
  activityReference.get()?.let { activity ->
    activity.runOnUiThread {
      listener.onActivityAvailable(activity)
      // Add this line to replicate issue in Development
      listener.onActivityAvailable(activity)
    }
  }
}