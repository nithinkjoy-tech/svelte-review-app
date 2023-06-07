<script>
  import FeedbackForm from "./components/FeedbackForm.svelte";
  import FeedbackList from "./components/FeedbackList.svelte";
  import FeedbackStats from "./components/FeedbackStats.svelte";

  let type = "text";
  let disabled = true;

  let feedback = [
    {
      id: 1,
      rating: 4.5,
      text: "Great product! Highly recommend.",
    },
    {
      id: 2,
      rating: 3.8,
      text: "Decent performance but could be better.",
    },
    {
      id: 3,
      rating: 5,
      text: "Excellent service! Will definitely come back.",
    },
  ];

  $: count = feedback.length;
  $: average = feedback.reduce((a, {rating}) => a + rating, 0) / count;

  let deleteFeedback = e => {
    const itemId = e.detail;
    feedback = feedback.filter(item => item.id !== itemId);
  };

  let addFeedback = ({detail:{rating,review}}) => {
    feedback = [
      ...feedback,
      {id: feedback.length + 1, rating: rating, text: review},
    ];
  };
</script>

<main class="container">
  <FeedbackForm on:addFeedback={addFeedback} {type} {disabled} />
  <FeedbackStats {average} {count} />
  <FeedbackList {feedback} on:delete-feedback={deleteFeedback} />
</main>
