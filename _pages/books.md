---
layout: page
title: Reading List
permalink: /books
comments: false
---

<p class="lead mb-4">Here's what I've been reading lately — books I've finished, ones I'm still working through, and what's up next on my list. This is not a complete list, but I'll keep adding to it over time — I hope.</p>

<ul class="nav nav-tabs book-tabs mb-4" role="tablist">
  <li class="nav-item">
    <a class="nav-link active" data-toggle="tab" href="#currently-reading" role="tab">Currently Reading</a>
  </li>
  <li class="nav-item">
    <a class="nav-link" data-toggle="tab" href="#want-to-read" role="tab">Want to Read</a>
  </li>
  <li class="nav-item">
    <a class="nav-link" data-toggle="tab" href="#all-books" role="tab">All</a>
  </li>
</ul>

<div class="tab-content">
  <div class="tab-pane fade show active" id="currently-reading" role="tabpanel">
    <div class="row">
      {% assign reading_books = site.data.books | where: "status", "reading" %}
      {% for book in reading_books %}
      {% include bookcard.html book=book %}
      {% endfor %}
      {% if reading_books.size == 0 %}
      <div class="col-12">
        <p class="text-muted">No books currently being read.</p>
      </div>
      {% endif %}
    </div>
  </div>
  <div class="tab-pane fade" id="want-to-read" role="tabpanel">
    <div class="row">
      {% assign want_books = site.data.books | where: "status", "want" %}
      {% for book in want_books %}
      {% include bookcard.html book=book %}
      {% endfor %}
      {% if want_books.size == 0 %}
      <div class="col-12">
        <p class="text-muted">No books in the queue yet.</p>
      </div>
      {% endif %}
    </div>
  </div>
  <div class="tab-pane fade" id="all-books" role="tabpanel">
    <div class="row">
      {% assign non_want_books = site.data.books | where_exp: "book", "book.status != 'want'" %}
      {% for book in non_want_books %}
      {% include bookcard.html book=book %}
      {% endfor %}
    </div>
  </div>
</div>

<script>
$('.book-tabs a[data-toggle="tab"]').on('click', function (e) {
  e.preventDefault();
  $(this).tab('show');
});
</script>
