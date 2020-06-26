# google-ads-in-recyclerview-example

class RecyclerViewAdsActivity : AppCompatActivity() {
    private var recyclerView: RecyclerView? = null
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_recycler_view_ads)
        recyclerView!!.layoutManager=LinearLayoutManager(this@RecyclerViewAdsActivity)
        val adapter=ItemArrayAdapter()
        recyclerView!!.adapter=adapter
    }
    private inner class ItemArrayAdapter// Constructor of the class
        (//All methods in this adapter are required for a bare minimum recyclerview adapter
    ) : RecyclerView.Adapter<ItemArrayAdapter.ViewHolder>() {

        // get the size of the list
        override fun getItemCount(): Int {
            return 5
        }


        // specify the row layout file and click for each row
        override fun onCreateViewHolder(parent: ViewGroup, viewType: Int): ViewHolder {
            val view = LayoutInflater.from(parent.context).inflate(R.layout.listing_item_ads, parent, false)
            return ViewHolder(view)
        }

        // load data in each row element
        @SuppressLint("SetTextI18n")
        override fun onBindViewHolder(holder: ViewHolder, position: Int) {
         holder.tv_title.text="Item name"

        }
        // Static inner class to initialize the views of rows
        internal inner class ViewHolder(itemView: View) : RecyclerView.ViewHolder(itemView), View.OnClickListener {
            var tv_title: TextView

            init {
                itemView.setOnClickListener(this)
                tv_title = itemView.findViewById(R.id.tv_title)
            }


            override fun onClick(view: View) {

            }
        }

    }
}


<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
        xmlns:app="http://schemas.android.com/apk/res-auto"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:background="@color/white"
        android:orientation="vertical"
        android:padding="@dimen/_10sdp">

    <ImageView
            android:id="@+id/iv_logo"
            android:layout_width="@dimen/_32sdp"
            android:layout_height="@dimen/_32sdp"
            android:src="@mipmap/ic_launcher"
            app:layout_constraintLeft_toLeftOf="parent"
            app:layout_constraintTop_toTopOf="parent" />

    <TextView
            android:id="@+id/tv_title"
            android:layout_width="0dp"
            android:layout_height="wrap_content"
            android:layout_marginLeft="@dimen/_5sdp"
            android:layout_marginRight="@dimen/_5sdp"
            android:text="Item Name"
            android:textColor="@color/black"
            android:textSize="@dimen/_15ssp"
            app:layout_constraintLeft_toRightOf="@+id/iv_logo"
            app:layout_constraintTop_toTopOf="parent" />
    <com.google.android.gms.ads.AdView xmlns:ads="http://schemas.android.com/apk/res-auto"
            android:id="@+id/adView"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:layout_marginTop="@dimen/_10sdp"
            ads:adSize="200x200"
            app:layout_constraintLeft_toRightOf="@+id/iv_logo"
            app:layout_constraintTop_toBottomOf="@+id/tv_title"
            android:layout_gravity="center_horizontal"
            ads:adUnitId="@string/banner_id"/>

</androidx.constraintlayout.widget.ConstraintLayout>
